# RockPaperScissorsc-
Rock Paper Scissors

using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace Rock_paper_scissors
{
    public partial class Form1 : Form
    {

        string weapon_player1 = ""; // weapon choice of player 1 
        string weapon_player2 = ""; // weapon choice of player 2
        string weapon_ai = ""; // weapon choice of computer
        int Ai = 0; // An integer to define if the game is going to be against a computer

        //  Random

        string[] weapons = { "Rock", "Paper", "Scissors" }; // array of weapon choices 

        Random random = new Random(); 
   

        public Form1() // As soon as the form is started most of the features are hidden except the pvp and Ai button
        {

            InitializeComponent();

            pictureBox1.Hide();// paper 
            pictureBox2.Hide();// scissors
            pictureBox3.Hide();// rock

            pictureBox4.Hide();// rock on top half
            pictureBox5.Hide();// scissors on top half
            pictureBox6.Hide();// paper on top half


          
            Rockbutton.Visible = false ; // 
            Paperbutton.Visible = false; // At start all buttons invisible (for player 1)
            Scissorsbutton.Visible = false; //

            Rockbutton2.Visible = false; //
            Paperbutton2.Visible = false; // At start all buttons invisible (for player 2)
            Scissorsbutton2.Visible = false; //

            Player1tag.Visible = false;// invisible tags (player 1 and 2)
            Player2tag.Visible = false;//

            Winnerdisp.Visible = false;// displays the winner label 
            Restartbutton.Visible = false;// displays the Menu button
            Continuebutton.Visible = false;// displays the continue button
            Instructions.Visible = false;

        }

        private void Pvpbutton_Click(object sender, EventArgs e) // if the player presses the pvp button
        {
            Pvpbutton.Hide(); // if pvp button chosen make all the buttons visible (player 1) and hide pvp and ai button 
            Aibutton.Hide(); //

            Instructions.Visible = true;


            Rockbutton.Visible = true;
            Paperbutton.Visible = true;// At start all buttons visible (for player 1)
            Scissorsbutton.Visible = true;

            Player1tag.Visible = true;// visible tags (player 1 and 2)
            Player2tag.Visible = true;//

        }

        private void Aibutton_Click(object sender, EventArgs e)// if the player presses the ai(computer) button
        {
            Ai = Ai + 1;// assigns Ai to be not a 0 so that the program knows if the user is playing against a computer

            Instructions.Visible = true;

            Pvpbutton.Hide(); // if pvp button chosen make all the buttons visible (player 1 and 2) and hide pvp and ai button 
            Aibutton.Hide(); //

            Rockbutton.Visible = true;
            Paperbutton.Visible = true;// At start all buttons invisible (for player 1)
            Scissorsbutton.Visible = true;

            Player2tag.Text = "Computer";//changing the player 2 tag to be a computer player tag
            Player1tag.Visible = true;// visible tag (player 1)
            Player2tag.Visible = true;// visible tag (player computer)

            int random_weapon = random.Next(0, weapons.Length); // generates a random number with the same range in the weapons list
            weapon_ai = weapons[random_weapon];// the random number is used as a key to get a random weapon
        //    MessageBox.Show(weapon_ai);

        }

        private void Paperbutton_Click(object sender, EventArgs e)
        {
            weapon_player1 = "Paper"; // if player 1 has chose paper he assigns his weapon variable that weapon
            Rockbutton.Visible = false; // 
            Paperbutton.Visible = false; // At start all buttons invisible (for player 1)
            Scissorsbutton.Visible = false; //
            if (Ai == 0) // if the player is not playing against a computer
            {
                Rockbutton2.Visible = true;
                Paperbutton2.Visible = true;// Make the player 2 buttons visible
                Scissorsbutton2.Visible = true;
            }
            else// player plays against player 2
            {
                if (weapon_ai == "Rock") // if ai choses rock 
                {
                    pictureBox3.Show(); // shows the rock picture for computer
                    Winnerdisp.Text = "Winner Player 1"; // displays the conclusion of the game
                    resultwin.Text = " Paper Covers Rock"; // explanation of how the winner won

                }
                else if (weapon_ai == "Paper")// if ai chooses paper
                {
                    pictureBox1.Show();// shows the rock picture of paper for computer
                    Winnerdisp.Text = "Draw";
                                
                }
                else
                {
                    pictureBox2.Show();
                    Winnerdisp.Text = "Winner Computer"; // if ai chooses Scissors 
                    resultwin.Text = "Scissors Cut Paper";// displays the conclusion of the game

                }
                pictureBox6.Show();//show the picture of a paper for player 1
                Winnerdisp.Visible = true;// display winner label
                Restartbutton.Visible = true;// display Menu/restart button
                Continuebutton.Visible = true;// display continue button
            }

        }

        private void Rockbutton_Click(object sender, EventArgs e)
        {
            weapon_player1 = "Rock";// if player 1 has chose rock he assigns his weapon variable that weapon
            Rockbutton.Visible = false; // 
            Paperbutton.Visible = false; // At start all buttons invisible (for player 1)
            Scissorsbutton.Visible = false; //

            if (Ai == 0)// if the player is not playing against a computer
            {
                Rockbutton2.Visible = true;
                Paperbutton2.Visible = true;// Make the player 2 buttons visible
                Scissorsbutton2.Visible = true;
            }
            else// player plays against player 2
            {
                if (weapon_ai == "Rock") // if ai choses rock 
                {
                    pictureBox3.Show();
                    Winnerdisp.Text = "Draw";
                    
                }
                else if (weapon_ai == "Paper")// if ai chooses paper
                {
                    pictureBox1.Show();
                    Winnerdisp.Text = "Winner Computer";
                    resultwin.Text = " Paper Covers Rock";

                }
                else
                {
                    pictureBox2.Show();
                    Winnerdisp.Text = "Winner Player 1"; // if ai chooses Scissors 
                    resultwin.Text = "Rock Breaks Scissors";
                }
                pictureBox4.Show(); //show the picture of a rock for player 1
                Winnerdisp.Visible = true;// display winner label
                Restartbutton.Visible = true;
                Continuebutton.Visible = true;
            }

        }

        private void Scissorsbutton_Click(object sender, EventArgs e)
        {
            weapon_player1 = "Scissors";// if player 1 has chose scissors he assigns his weapon variable that weapon
            Rockbutton.Visible = false; // 
            Paperbutton.Visible = false; // At start all buttons invisible (for player 1)
            Scissorsbutton.Visible = false; // 
            if (Ai == 0)// if the player is not playing against a computer
            {
                Rockbutton2.Visible = true;
                Paperbutton2.Visible = true;// Make the player 2 buttons visible
                Scissorsbutton2.Visible = true;
            }
            else// player plays against player 2
            {
                if (weapon_ai == "Rock") // if ai choses rock 
                {
                    pictureBox3.Show();//rock
                    Winnerdisp.Text = "Winner Player 1"; // if ai chooses Scissors 
                    resultwin.Text = "Scissors Cut Paper";

                }
                else if (weapon_ai == "Paper")// if ai chooses paper
                {
                    pictureBox1.Show();
                    Winnerdisp.Text = "Winner Player 1"; // if ai chooses Scissors 
                    resultwin.Text = "Scissors Cut Paper";

                }
                else
                {
                    pictureBox2.Show();
                    Winnerdisp.Text = "Draw";

                }
                pictureBox5.Show();// //show the picture of a scissors for player 1
                Winnerdisp.Visible = true;
                Restartbutton.Visible = true;
                Continuebutton.Visible = true;
            }

        }

        private void Rockbutton2_Click(object sender, EventArgs e)
        {
            weapon_player2 = "Rock";// if player 2 has chose rock he assigns his weapon variable that weapon
            Rockbutton.Visible = false; // 
            Paperbutton.Visible = false; // At start all buttons invisible (for player 1)
            Scissorsbutton.Visible = false; //
            Rockbutton2.Visible = false; //
            Paperbutton2.Visible = false; // At start all buttons invisible (for player 2)
            Scissorsbutton2.Visible = false; //
            if (weapon_player1 == "Rock") // if player 1 choses rock 
            {
                pictureBox3.Show();
                Winnerdisp.Text = "Draw";

            }
            else if (weapon_player1 == "Paper")// if player 1 chooses paper
            {
                pictureBox1.Show();//
                Winnerdisp.Text = "Winner Player 1";
                resultwin.Text = "Paper Covers Rock ";
            }
            else
            {
                pictureBox2.Show();
                Winnerdisp.Text = "Winner Player 2"; // if player 1 chooses Scissors 
                resultwin.Text = "Scissors Cut Paper ";

            }
            pictureBox4.Show();//show the picture of a rock for player 2
            Winnerdisp.Visible = true;
            Restartbutton.Visible = true;
            Continuebutton.Visible = true;
          
            
        }

        private void Paperbutton2_Click(object sender, EventArgs e)
        {
            weapon_player2 = "Paper";// if player 2 has chose paper he assigns his weapon variable that weapon
            Rockbutton.Visible = false; // 
            Paperbutton.Visible = false; // At start all buttons invisible (for player 1)
            Scissorsbutton.Visible = false; //
            Rockbutton2.Visible = false; //
            Paperbutton2.Visible = false; // At start all buttons invisible (for player 2)
            Scissorsbutton2.Visible = false; //
            if (weapon_player1 == "Rock")
            {
                pictureBox3.Show();
                Winnerdisp.Text = "Winner Player 2"; // if player 1 chooses rock 
                resultwin.Text = "Paper Covers Rock ";
            }
            else if (weapon_player1 == "Paper")// if player 1 chooses paper
            {
                pictureBox1.Show();
                Winnerdisp.Text = "Draw";
            }
            else
            {
                pictureBox2.Show();
                Winnerdisp.Text = "Winner Player 1"; // if player 1 chooses Scissors 
                resultwin.Text = "Scissors Cut Paper ";
            }
            pictureBox6.Show();// paper player 1
            Winnerdisp.Visible = true;
            Restartbutton.Visible = true;
            Continuebutton.Visible = true;
        }

        private void Scissorsbutton2_Click(object sender, EventArgs e)
        {
            weapon_player2 = "Scissors";// if player 2 has chose scissors he assigns his weapon variable that weapon
            Rockbutton.Visible = false; // 
            Paperbutton.Visible = false; // At start all buttons invisible (for player 1)
            Scissorsbutton.Visible = false; // 
            Rockbutton2.Visible = false; //
            Paperbutton2.Visible = false; // At start all buttons invisible (for player 2)
            Scissorsbutton2.Visible = false; //
            if (weapon_player1 == "Rock")
            {
                pictureBox3.Show();
                Winnerdisp.Text = "Winner Player 1"; // if player 1 choses rock 
                resultwin.Text = "Rock Breaks Scissors ";
            }
            else if (weapon_player1 == "Paper")// if player 1 choses paper
            {
                pictureBox1.Show();
                Winnerdisp.Text = "Winner Player 2";
                resultwin.Text = "Scissors Cut Paper ";
            }
            else
            {
                pictureBox2.Show();
                Winnerdisp.Text = "Draw"; // if player 1 choses Scissors 
            }
            pictureBox5.Show();// scissors player 1
            Winnerdisp.Visible = true;
            Restartbutton.Visible = true;
            Continuebutton.Visible = true;

        }

        private void Winnerdisp_Click(object sender, EventArgs e)
        {

        }

        private void Restartbutton_Click(object sender, EventArgs e)
        {
            Ai = 0;
            pictureBox1.Hide();// paper
            pictureBox2.Hide();// scissors
            pictureBox3.Hide();// rock

            pictureBox4.Hide();// rock
            pictureBox5.Hide();// scissors
            pictureBox6.Hide();// paper

            Rockbutton.Visible = false; // 
            Paperbutton.Visible = false; // At start all buttons invisible (for player 1)
            Scissorsbutton.Visible = false; //

            Rockbutton2.Visible = false; //
            Paperbutton2.Visible = false; // At start all buttons invisible (for player 2)
            Scissorsbutton2.Visible = false; //

            Player1tag.Visible = false;// invisible tags (player 1 and 2)
            Player2tag.Visible = false;//

            Winnerdisp.Visible = false;// displays the winner label is hidden
            Restartbutton.Visible = false;
            resultwin.Visible = false;
            Instructions.Visible = false;
            Continuebutton.Visible = false;
            Pvpbutton.Show(); // if pvp button chosen make all the buttons visible (player 1 and 2) and hide pvp and ai button 
            Aibutton.Show(); //
        }

        private void Continuebutton_Click(object sender, EventArgs e)
        {
            int random_weapon = random.Next(0, weapons.Length);
            weapon_ai = weapons[random_weapon]; // generates a differnt random number for a computer to choose a different weapon
            Continuebutton.Visible = false;
           
            Rockbutton.Visible = true;
            Paperbutton.Visible = true;
            Scissorsbutton.Visible = true;
            Player1tag.Visible = true;// visible tags (player 1 and 2)
            Player2tag.Visible = true;//
            Winnerdisp.Visible = false;// displays the winner label is hidden
            Restartbutton.Visible = false;
            resultwin.Visible = false;

            pictureBox1.Hide();// paper
            pictureBox2.Hide();// scissors
            pictureBox3.Hide();// rock

            pictureBox4.Hide();// rock
            pictureBox5.Hide();// scissors           
            pictureBox6.Hide();// paper

        }


    }
}
