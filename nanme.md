<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CRUD API Test</title>
    <style>
        /* สไตล์เหมือนเดิม */
    </style>
    <script>
        let currentEditId = null; // Variable to store the ID of the current editing user

        // Fetch data from MongoDB and display it
        async function fetchData() {
            const response = await fetch('/api/data');
            const data = await response.json();
            const container = document.getElementById('data-list');
            container.innerHTML = '';
            data.forEach(item => {
                const div = document.createElement('div');
                div.className = 'data-item';
                div.innerHTML = `
                    <span style="flex-grow: 1;">Name: ${item.name}, Email: ${item.email}, Age: ${item.age}, Message: ${item.message || 'N/A'}</span>
                    <button onclick="editData('${item._id}', '${item.name}', '${item.email}', ${item.age}, '${item.message || ''}')">Edit</button>
                    <button onclick="deleteData('${item._id}')">Delete</button>
                `;
                container.appendChild(div);
            });
        }

        // Add new data to MongoDB
        async function addData() {
            // โค้ดเหมือนเดิม
        }

        // Edit data in MongoDB
        async function editData(id, name, email, age, message) {
            // โค้ดเหมือนเดิม
        }

        // Update data in MongoDB
        async function updateData() {
            // โค้ดเหมือนเดิม
        }

        // Delete data from MongoDB
        async function deleteData(id) {
            if (id) {
                await fetch(`/api/data/${id}`, {
                    method: 'DELETE',
                });
                clearFields(); // Clear fields after deletion
                fetchData(); // Refresh the data after deleting
            } else {
                alert("Please select a user to delete.");
            }
        }

        // Clear input fields
        function clearFields() {
            // โค้ดเหมือนเดิม
        }

        // Load data when the page loads
        window.onload = fetchData;
    </script>
</head>
<body>
    <div class="container">
        <h1>CRUD API Test</h1>
        <h2>Add New User</h2>
        <div class="input-group">
            <input type="text" id="name" placeholder="Name">
            <input type="text" id="email" placeholder="Email">
            <input type="number" id="age" placeholder="Age" min="0">
        </div>
        <textarea id="message" placeholder="Message"></textarea>
        <br>
        <button onclick="addData()">Add User</button>
        <button onclick="updateData()" style="background-color: #f57c00;">Update User</button>
        <button onclick="deleteData(currentEditId)" style="background-color: #f57c00;">Delete User</button>
        <button onclick="fetchData()" style="background-color: #f57c00;">Read User</button>

        <h2>Users</h2>
        <div class="data-container" id="data-list"></div>
    </div>
</body>
</html>

</html>


