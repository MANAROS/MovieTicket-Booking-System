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

 20
