# movie-ticket-booking-system-Netbeans

In this project movie ticket is booked  using  movie Ticket booking system. We enter into Web page by logging with User Name and Password. 
Then we select the Movie and later in which Theatre movie is running. Later choose Show Timings and enter no of tickets you want .
Finally it displays the details of the procedure and print the form to show at respective ticket counter to get ticket. 

<img width="827" alt="2024-10-23 (2)" src="https://github.com/user-attachments/assets/f678a4fe-51b1-48ba-b5c8-a81b9707556b">

# Code-Snippet-and-Examples
## 1.Login

private void submitActionPerformed(java.awt.event.ActionEvent evt) {                                         
    String username = jTextField1.getText(); // Get the username from the text field
    String password = new String(jPasswordField1.getPassword()); // Get the password from the password field

    try {
        // Load the MySQL JDBC driver
        Class.forName("com.mysql.cj.jdbc.Driver");

        // Connect to the database
        Connection c = DriverManager.getConnection("jdbc:mysql://localhost/java_dbmovies", "root", "");

        // Create the query
        String query = "SELECT name, password FROM register WHERE name=? AND password=?";
        PreparedStatement pst = c.prepareStatement(query);
        pst.setString(1, username);
        pst.setString(2, password);

        // Execute the query and check the result
        ResultSet rs = pst.executeQuery();
        
        if (rs.next()) {
            // If the user is found, login successfully
            JOptionPane.showMessageDialog(this, "Logged in successfully");
            this.setVisible(false); // Hide the login window
            new movie().setVisible(true); // Open the movie window
        } else {
            // If credentials are invalid
            JOptionPane.showMessageDialog(this, "Invalid username or password");
        }

    } catch (Exception e) {
        e.printStackTrace(); // Print any exceptions
    }
}

Example Used:
 • Allows users to input their username and password.
 • Validates user credentials by checking against a database.
 • Displays a message when login is successful or when the credentials are incorrect.

 
 ## 2.Card Selction 
 class CardSelection extends JFrame {
    public CardSelection() {
        JRadioButton rbCredit = new JRadioButton("Credit Card");
        JRadioButton rbDebit = new JRadioButton("Debit Card");
        JButton btnPay = new JButton("Make Payment");

        ButtonGroup group = new ButtonGroup();
        group.add(rbCredit);
        group.add(rbDebit);
Example Usage:
A group of buttons is created and only one button can always be selected at a time. This is useful in cases where the user needs to select only one option from several.


## 3.Cancel:
import javax.swing.*;

public class CancelBooking extends JFrame {
    public CancelBooking() {
        initComponents();
    }

    private void initComponents() {
        JLabel label1 = new JLabel("YOUR BOOKING IS CANCELLED");
        JLabel label2 = new JLabel("PLEASE VISIT AGAIN");
        JButton btnClose = new JButton("Close");

        label1.setFont(new java.awt.Font("Times New Roman", 1, 36));
        label2.setFont(new java.awt.Font("Algerian", 1, 24));

        btnClose.addActionListener(evt -> dispose());

        JPanel panel = new JPanel();
        panel.add(label1);
        panel.add(label2);
        panel.add(btnClose);

        add(panel);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        pack();
    }

    public static void main(String[] args) {
        new CancelBooking().setVisible(true);
    }
}
Example Usage : 
This will open a window displaying two messages: "YOUR BOOKING IS CANCELLED" at the top and "PLEASE VISIT AGAIN" at the bottom

## 4.Moviebooking
private void jButton1ActionPerformed(java.awt.event.ActionEvent evt) {
    String selectedMovie = (String) jComboBox1.getSelectedItem();
    String selectedTheatre = (String) jComboBox2.getSelectedItem();
    String selectedTime = (String) jComboBox3.getSelectedItem();
    String selectedDate = (String) jComboBox4.getSelectedItem();
    
    try {
        int numberOfTickets = Integer.parseInt(jTextField1.getText());
        
        if (numberOfTickets > 0 && numberOfTickets < 10) {
            this.setVisible(false);
            new Receipt(selectedMovie, selectedTheatre, selectedTime, selectedDate, numberOfTickets * 100).setVisible(true);
            updateTicketsInDatabase(selectedTheatre, selectedTime, numberOfTickets);
        } else {
            System.out.println("Please enter a valid number of tickets (1-9).");
        }
    } catch (NumberFormatException e) {
        System.out.println("Invalid input for number of tickets.");
    }
}
Example Usage:
wWhen a user selects the movie, theatre, time, date, and enters the number of tickets, the program will validate and attempt to update the database with the remaining ticket count.

## 5.Receipt 
import javax.swing.*;

public class TicketBookingApp {
    public static void main(String[] args) {
        // Ticket details
        String movie = "Inception"; // Movie name
        String theatre = "Cineworld"; // Theatre name
        String showTime = "7:00 PM"; // Show time
        String date = "2024-10-25"; // Date of the show
        int numberOfTickets = 2; // Number of tickets
        String fare = "$15.00"; // Ticket fare

        // Create the receipt and pass the details
        recepit receipt = new recepit(movie, theatre, showTime, date, numberOfTickets, fare);
        receipt.setVisible(true); // Display the receipt
    }
}



    
