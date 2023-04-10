# -Database-Design
Migration plan for v2:

Alter the 'playlists' table to allow users to have multiple playlists by adding a name field for playlists.

ALTER TABLE playlists ADD name VARCHAR(255) NOT NULL;

Create a new table 'account_types' to store different account types with their respective privileges. Add a foreign key in the 'users' table referencing the account_types table.

CREATE TABLE account_types (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(255) NOT NULL UNIQUE
);

ALTER TABLE users ADD account_type_id INT NOT NULL;
ALTER TABLE users ADD FOREIGN KEY (account_type_id) REFERENCES account_types(id);

Populate the 'account_types' table with the possible account types (e.g., free, standard, premium).
With these changes, the schema will support multiple playlists per user and different account types for users, addressing the business requirements for v2.

