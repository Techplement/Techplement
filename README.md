def Database():
    connectn = sqlite3.connect("contactdata.db")
    cursor = connectn.cursor()
    cursor.execute("CREATE TABLE IF NOT EXISTS `contactinformation` (id INTEGER NOT NULL PRIMARY KEY AUTOINCREMENT, first_name TEXT, middle_name TEXT, last_name TEXT, gender TEXT, age TEXT, home_address TEXT, phone_number TEXT)")
    cursor.execute("SELECT * FROM `contactinformation` ORDER BY `last_name` ASC")
    fetchinfo = cursor.fetchall()
    for data in fetchinfo:
        tree.insert('', 'end', values=(data))
    cursor.close()
    connectn.close()
def Submit():
if f_name.get() == "" or m_name.get() == "" or l_name.get() == "" or gender.get() == "" or age.get() == "" or home_address.get() == "" or phone_number.get() == "" or religion.get() == "" or nationality.get() == "":
result = tkMessageBox.showwarning('', 'Please Complete The Required Field', icon="warning")
else:
tree.delete(*tree.get_children())
conn = sqlite3.connect("contactdb.db")
cursor = conn.cursor()
cursor.execute(
"INSERT INTO `contactable` (first_name, middle_name, last_name, gender, age, home_address, phone_number, religion, nationality) VALUES(?, ?, ?, ?, ?, ?, ?, ?, ?)", (str(f_name.get()), str(m_name.get()), str(l_name.get()), str(gender.get()), int(age.get()), str(home_address.get()),
int(phone_number.get()), str(religion.get()), str(nationality.get())))
conn.commit()
cursor.execute("SELECT * FROM `contactable` ORDER BY `last_name` ASC")
fetch = cursor.fetchall()
for data in fetch:
tree.insert('', 'end', values=(data))
cursor.close()
conn.close()
f_name.set("")
m_name.set("")
l_name.set("")
gender.set("")
age.set("")
home_address.set("")
phone_number.set("")
religion.set("")
nationality.set("")
