# AddressBook
#User can add and search name, phone, email, ...etc.

"""ADDRESS BOOK
"""

def append_to_database (info):
    """This function adds or appends the info list
       to the file.
    """
    
    temp1 = open("addressbook.txt","a")
    temp1.write(info)
    temp1.write("\n")

    print ("The record was added to the database address book ")



def collect ():
    """This function collects information
       & appends to the file.
    """
        
    lastname = raw_input("What is the person's last name? ")
    firstname = raw_input("What is the person's first name? ")
    phone = input("What is the person's phone number? ")
    email = raw_input("What is the person's email address? ")
    address = raw_input("What is the person's address? ")

    info = (firstname + " " + lastname + ", " + str(phone) + ", " + email + ", " + "( " + address + " )")
    
    append_to_database (info)


def browse_contacts():
    """This function lets us see all the list of
       contacts.
    """ 
    print("Alright, so this is where you will see a list of all your contacts, and all their information.")

    temp1 = open("addressbook.txt", "r")
    readfile = temp1.read()

    print (readfile)

    reset()

def search_contact():
    """This function Searches a single contact.
    """
    
    print("Alright, so here is where you would search for people already in the address book.")
    
    criteria = raw_input("Please enter any keywords, including address, phone number, etc. for the search: ")
    
    temp1 = open("addressbook.txt", "r+")
    
    for line in temp1:

        if criteria.lower() in line:

            print line
            reset()

    else:
        print("Did not find person. \n Please add him/her/it to the address book first.")
            
    reset()


def reset():
    """This function resets the program and start
       another operation.
    """
    
    userinput = raw_input("Would you like to restart the program to perform another operation? Press 'y' OR Press 'n'] ")

    if userinput == 'y':
        main()

    elif userinput == 'n':
        print("Your addressbook will close.")

    else:
        print("Not a valid command.")
        reset()



def main ():
    """To ask the user what to do
    """
    
    answer = input("Do You Want To Create An Entry [Press 1] \nOr Do You Want to Browse All Contacts [Press 2] \nOr Do You Want To Search A Single Person [Press 3] :- ")
    
    if answer == 1:
        collect ()

    if answer == 2:
        browse_contacts()

    if answer == 3:
        search_contact()

    else:

        print str(answer) + " is not a valid option, try again"
        main()   


#Main starts from here
main ()
