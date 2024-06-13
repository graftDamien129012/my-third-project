# my-third-project
using System;
using System.Windows.Forms;

namespace AIWritingDetector
{
    public partial class MainForm : Form
    {
        private TextBox textInput;
        private Button detectButton;
        private Label resultLabel;

        public MainForm()
        {
            InitializeComponent();
        }

        private void InitializeComponent()
        {
            this.textInput = new TextBox();
            this.detectButton = new Button();
            this.resultLabel = new Label();
            this.SuspendLayout();

            this.textInput.Location = new System.Drawing.Point(10, 10);
            this.textInput.Multiline = true;
            this.textInput.Size = new System.Drawing.Size(300, 150);
            this.textInput.PlaceholderText = "Enter text...";
            this.Controls.Add(this.textInput);

            this.detectButton.Location = new System.Drawing.Point(120, 180);
            this.detectButton.Size = new System.Drawing.Size(80, 30);
            this.detectButton.Text = "Detect";
            this.detectButton.Click += new System.EventHandler(this.DetectButton_Click);
            this.Controls.Add(this.detectButton);

            this.resultLabel.AutoSize = true;
            this.resultLabel.Location = new System.Drawing.Point(10, 230);
            this.resultLabel.Text = "";
            this.Controls.Add(this.resultLabel);

            this.ClientSize = new System.Drawing.Size(320, 260);
            this.FormBorderStyle = System.Windows.Forms.FormBorderStyle.FixedSingle;
            this.MaximizeBox = false;
            this.Name = "MainForm";
            this.Text = "AI Writing Detector";
            this.ResumeLayout(false);
            this.PerformLayout();
        }

        private void DetectButton_Click(object sender, EventArgs e)
        {
            string text = textInput.Text.ToLower();
            string result = text.Contains("ai") ? "AI writing detected" : "Human writing detected";
            resultLabel.Text = result;
        }
    }

    public class Program
    {
        [STAThread]
        static void Main()
        {
            Application.EnableVisualStyles();
            Application.SetCompatibleTextRenderingDefault(false);
            Application.Run(new MainForm());
        }
    }
}
