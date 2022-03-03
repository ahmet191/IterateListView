# IterateListView
It's about how to iterate ListView in c# WinForm

Hello dear reader,
 I will mention some problem that i have faced and i couldn't find the clear solution for this.
 Accually it is too simple but it is kinda tricky if you don't know
 
 As you propable already know listView in winform also act like List but ofcourse those both are different types.
 But we can iterate both with for loop easily but there is problem with listView when it comes to iterate with foreach loop
 ın for each loop we have to declare the type of data we will iterate. in list it is easy. We can use "var" for sure 
 if we don't know the type. But in this point listview make things difficult because it doesn't matter what is inside of listView. You have to declare exact data type in its own way only.
 But let's make this easier to understand with example
 
 
        private void Form1_Load(object sender, EventArgs e) // First create an listView and 3 textBox
        {
            listView1.View = View.Details;
            listView1.FullRowSelect = true;
            listView1.Columns.Add("Ad", 150);
            listView1.Columns.Add("Soyad", 150);
            listView1.Columns.Add("Meslek", 150);
        }


private void button1_Click(object sender, EventArgs e) // just button to add some data into listView
        {
            string ad = textBox1.Text;
            string soyad = textBox2.Text;
            string meslek = textBox3.Text;
            string[] bilgiler = { ad, soyad, meslek };
            listView1.Items.Add(new ListViewItem(bilgiler));
            MessageBox.Show("Kayıt Eklendi.");
            textBox1.Clear();
            textBox2.Clear();
            textBox3.Clear();
        }


        private void button2_Click(object sender, EventArgs e) // This is first scenario with two "foreach" usage
        {

            string test = "";
            foreach (ListViewItem item in listView1.Items) //We
            {
                foreach (ListViewItem.ListViewSubItem subitem in item.SubItems)
                {
                    test += " " + subitem.Text;
                }
            }
            MessageBox.Show(test); // for testing purpose and know we can reach the every item inside listView
        }


        private void button3_Click(object sender, EventArgs e) // This is second scenario with one "foreach" one "for" usage
        {
            string test2 = "";
            foreach (ListViewItem item in listView1.Items) //We
            {
                for (int i = 0; i < item.SubItems.Count; i++)
                {

                    test2 += " " + item.SubItems[i].Text;
                }
            }
            MessageBox.Show(test2); // for testing purpose and know we can reach the every item inside listView
        }
        
        
        private void button5_Click(object sender, EventArgs e) // This is third scenario with one "foreach" one "for" usage
        {
            string test4 = "";
            for (int i = 0; i < listView1.Items.Count; i++)
            {
                foreach (ListViewItem.ListViewSubItem subitem in listView1.Items[i].SubItems)
                {
                    test4 += " " + subitem.Text;
                }
            }
            MessageBox.Show(test4); // for testing purpose and know we can reach the every item inside listView
        } 


        private void button4_Click(object sender, EventArgs e) // This is fourth scenario with two "for" usage
        {
            string test3 = "";
            for (int i = 0; i < listView1.Items.Count; i++)
            {
                for (int j = 0; j < listView1.Items[i].SubItems.Count; j++)
                {

                    test3 += " " + listView1.Items[i].SubItems[j].Text;
                }
            }
            MessageBox.Show(test3); // for testing purpose and know we can reach the every item inside listView
        }

