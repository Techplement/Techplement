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
