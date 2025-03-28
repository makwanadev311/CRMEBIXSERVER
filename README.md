<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Admin Portal</title>
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Arial', sans-serif;
        }
        
        body {
            background-color: #f5f5f5;
            min-height: 100vh;
            position: relative;
            padding-bottom: 60px;
        }
        
        .container {
            width: 95%;
            max-width: 1200px;
            margin: 0 auto;
        }
        
        /* Login Page Styles */
        .login-container {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }
        
        .login-form {
            background-color: white;
            padding: 30px;
            border-radius: 8px;
            box-shadow: 0 0 15px rgba(0,0,0,0.1);
            width: 350px;
        }
        
        .login-form h2 {
            text-align: center;
            margin-bottom: 25px;
            color: #333;
        }
        
        .form-group {
            margin-bottom: 20px;
        }
        
        .form-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: bold;
            color: #555;
        }
        
        .form-group input {
            width: 100%;
            padding: 12px;
            border: 1px solid #ddd;
            border-radius: 4px;
            font-size: 16px;
        }
        
        .btn {
            background-color: #4CAF50;
            color: white;
            padding: 12px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            width: 100%;
            font-size: 16px;
            font-weight: bold;
            transition: background-color 0.3s;
        }
        
        .btn:hover {
            background-color: #45a049;
        }
        
        /* Dashboard Styles */
        .dashboard {
            display: none;
        }
        
        .header {
            background-color: #4CAF50;
            color: white;
            padding: 15px 20px;
            border-radius: 8px 8px 0 0;
            margin-top: 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .user-actions {
            display: flex;
            gap: 15px;
            align-items: center;
        }
        
        .user-actions a {
            color: white;
            text-decoration: none;
            font-size: 14px;
        }
        
        /* Stats Cards */
        .stats {
            display: flex;
            justify-content: space-between;
            margin: 25px 0;
            gap: 15px;
        }
        
        .stat-box {
            background-color: white;
            padding: 20px;
            border-radius: 6px;
            text-align: center;
            flex: 1;
            box-shadow: 0 0 5px rgba(0,0,0,0.1);
        }
        
        .stat-box h3 {
            margin-top: 0;
            color: #4CAF50;
            font-size: 16px;
        }
        
        .stat-box p {
            font-size: 24px;
            font-weight: bold;
            margin-bottom: 0;
            color: #333;
        }
        
        /* Form Sections */
        .form-section {
            background-color: white;
            padding: 20px;
            border-radius: 6px;
            margin-bottom: 25px;
            box-shadow: 0 0 5px rgba(0,0,0,0.1);
        }
        
        .form-section h2 {
            margin-top: 0;
            color: #333;
            font-size: 20px;
            margin-bottom: 20px;
        }
        
        .form-row {
            display: flex;
            gap: 15px;
            margin-bottom: 15px;
        }
        
        .form-row .form-group {
            flex: 1;
        }
        
        textarea {
            width: 100%;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 4px;
            font-family: Arial, sans-serif;
            resize: vertical;
            min-height: 80px;
        }
        
        select {
            width: 100%;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 4px;
            font-size: 16px;
            height: 42px;
        }
        
        /* Tabs */
        .tabs {
            display: flex;
            margin-bottom: 20px;
            border-bottom: 1px solid #ddd;
        }
        
        .tab-btn {
            padding: 10px 20px;
            background-color: #f1f1f1;
            border: none;
            cursor: pointer;
            transition: all 0.3s;
            font-size: 16px;
        }
        
        .tab-btn.active {
            background-color: #4CAF50;
            color: white;
        }
        
        .tab-content {
            display: none;
        }
        
        .tab-content.active {
            display: block;
        }
        
        /* Tables */
        .table-container {
            max-height: 500px;
            overflow-y: auto;
            margin-bottom: 20px;
            border: 1px solid #ddd;
            border-radius: 6px;
            background-color: white;
        }
        
        table {
            width: 100%;
            border-collapse: collapse;
        }
        
        th, td {
            padding: 12px 15px;
            text-align: left;
            border-bottom: 1px solid #ddd;
        }
        
        th {
            background-color: #4CAF50;
            color: white;
            position: sticky;
            top: 0;
        }
        
        tr:hover {
            background-color: #f9f9f9;
        }
        
        /* Action Buttons */
        .action-btn {
            padding: 6px 12px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-size: 14px;
            margin-right: 5px;
            transition: all 0.3s;
        }
        
        .accept-btn {
            background-color: #4CAF50;
            color: white;
        }
        
        .hold-btn {
            background-color: #FF9800;
            color: white;
        }
        
        .delete-btn {
            background-color: #f44336;
            color: white;
        }
        
        .print-btn {
            background-color: #2196F3;
            color: white;
        }
        
        /* Photo Preview */
        .photo-preview {
            width: 50px;
            height: 50px;
            object-fit: cover;
            border-radius: 4px;
        }
        
        /* Modals */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0,0,0,0.5);
            z-index: 100;
            justify-content: center;
            align-items: center;
        }
        
        .modal-content {
            background-color: white;
            padding: 25px;
            border-radius: 8px;
            width: 90%;
            max-width: 500px;
            box-shadow: 0 0 15px rgba(0,0,0,0.2);
        }
        
        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
        }
        
        .close {
            font-size: 24px;
            cursor: pointer;
            color: #777;
        }
        
        .close:hover {
            color: #333;
        }
        
        /* Footer */
        .footer {
            text-align: center;
            padding: 15px;
            background-color: gray;
            color: white;
            position: fixed;
            bottom: 0;
            width: 100%;
            font-size: 14px;
        }
        
        /* Print Styles */
        @media print {
            body * {
                visibility: hidden;
            }
            #printSection, #printSection * {
                visibility: visible;
            }
            #printSection {
                position: absolute;
                left: 0;
                top: 0;
                width: 100%;
            }
            .no-print {
                display: none !important;
            }
        }
        
        /* User Profile Section */
        .profile-section {
            background-color: white;
            padding: 20px;
            border-radius: 6px;
            margin-bottom: 25px;
            box-shadow: 0 0 5px rgba(0,0,0,0.1);
        }
        
        .profile-section h2 {
            margin-top: 0;
            color: #333;
            font-size: 20px;
            margin-bottom: 20px;
        }
    </style>
</head>
<body>
    <!-- Global Footer -->
    <footer class="footer">
        All Rights Reserved by Dev Makwana Ebixserver 2025
    </footer>

    <div class="container">
        <!-- Login Section -->
        <div class="login-container" id="loginSection">
            <div class="login-form">
                <h2>Admin Login</h2>
                <div class="form-group">
                    <label for="username">Username</label>
                    <input type="text" id="username" placeholder="Enter username" value="eraj12">
                </div>
                <div class="form-group">
                    <label for="password">Password</label>
                    <input type="password" id="password" placeholder="Enter password" value="12345">
                </div>
                <button class="btn" onclick="login()">Login</button>
            </div>
        </div>
        
        <!-- Dashboard Section -->
        <div class="dashboard" id="dashboard">
            <div class="header">
                <h1>Admin Portal - Machine & Customer Records</h1>
                <div class="user-actions">
                    <span id="displayUsername">eraj12</span>
                    <a href="#" onclick="showProfileModal()">Profile</a>
                    <a href="#" onclick="logout()">Logout</a>
                </div>
            </div>
            
            <!-- User Profile Section -->
            <div class="profile-section">
                <h2>User Profile</h2>
                <div class="form-row">
                    <div class="form-group">
                        <label for="profileUsername">Username</label>
                        <input type="text" id="profileUsername" placeholder="Username">
                    </div>
                    <div class="form-group">
                        <label for="profileEmail">Email</label>
                        <input type="email" id="profileEmail" placeholder="Email">
                    </div>
                </div>
                <button class="btn" onclick="updateProfile()">Update Profile</button>
                <button class="btn" onclick="showChangePasswordModal()" style="margin-top: 10px;">Change Password</button>
            </div>
            
            <!-- Stats Cards -->
            <div class="stats">
                <div class="stat-box">
                    <h3>Total Records</h3>
                    <p id="totalRecords">0</p>
                </div>
                <div class="stat-box">
                    <h3>Accepted Records</h3>
                    <p id="acceptedRecords">0</p>
                </div>
                <div class="stat-box">
                    <h3>Hold Records</h3>
                    <p id="holdRecords">0</p>
                </div>
            </div>
            
            <!-- Tabs -->
            <div class="tabs">
                <button class="tab-btn active" onclick="showTab('machine')">Machine Records</button>
                <button class="tab-btn" onclick="showTab('customer')">Customer Records</button>
            </div>
            
            <!-- Machine Records Tab -->
            <div id="machineTab" class="tab-content active">
                <div class="form-section">
                    <h2>Add New Machine Record</h2>
                    <div class="form-row">
                        <div class="form-group">
                            <label for="machineName">Machine Name</label>
                            <input type="text" id="machineName" placeholder="Enter machine name">
                        </div>
                        <div class="form-group">
                            <label for="serialNumber">Serial Number</label>
                            <input type="text" id="serialNumber" placeholder="Enter serial number">
                        </div>
                    </div>
                    
                    <div class="form-row">
                        <div class="form-group">
                            <label for="machinePhoto">Upload Photo</label>
                            <input type="file" id="machinePhoto" accept="image/*">
                        </div>
                        <div class="form-group">
                            <label for="machineType">Record Type</label>
                            <select id="machineType">
                                <option value="Purchase">Purchase</option>
                                <option value="Service">Service</option>
                                <option value="Warranty">Warranty</option>
                                <option value="Other">Other</option>
                            </select>
                        </div>
                    </div>
                    
                    <div class="form-group">
                        <label for="machineRemarks">Remarks</label>
                        <textarea id="machineRemarks" placeholder="Enter any remarks"></textarea>
                    </div>
                    
                    <button class="btn" onclick="addMachineRecord()">Add Machine Record</button>
                </div>
                
                <h2>Machine Records</h2>
                <div class="table-container">
                    <table id="machineTable">
                        <thead>
                            <tr>
                                <th>ID</th>
                                <th>Machine Name</th>
                                <th>Serial No.</th>
                                <th>Photo</th>
                                <th>Type</th>
                                <th>Status</th>
                                <th>Created At</th>
                                <th>Updated At</th>
                                <th>Remarks</th>
                                <th>Actions</th>
                            </tr>
                        </thead>
                        <tbody>
                            <!-- Machine records will be added here -->
                        </tbody>
                    </table>
                </div>
            </div>
            
            <!-- Customer Records Tab -->
            <div id="customerTab" class="tab-content">
                <div class="form-section">
                    <h2>Add New Customer Record</h2>
                    <div class="form-row">
                        <div class="form-group">
                            <label for="customerFirstName">First Name</label>
                            <input type="text" id="customerFirstName" placeholder="Enter first name">
                        </div>
                        <div class="form-group">
                            <label for="customerLastName">Last Name</label>
                            <input type="text" id="customerLastName" placeholder="Enter last name">
                        </div>
                    </div>
                    
                    <div class="form-row">
                        <div class="form-group">
                            <label for="customerContact">Contact Number</label>
                            <input type="text" id="customerContact" placeholder="Enter contact number">
                        </div>
                        <div class="form-group">
                            <label for="customerEmail">Email</label>
                            <input type="email" id="customerEmail" placeholder="Enter email">
                        </div>
                    </div>
                    
                    <div class="form-group">
                        <label for="customerAddress">Address</label>
                        <textarea id="customerAddress" placeholder="Enter full address"></textarea>
                    </div>
                    
                    <div class="form-row">
                        <div class="form-group">
                            <label for="customerCity">City</label>
                            <input type="text" id="customerCity" placeholder="Enter city">
                        </div>
                        <div class="form-group">
                            <label for="customerState">State</label>
                            <input type="text" id="customerState" placeholder="Enter state">
                        </div>
                        <div class="form-group">
                            <label for="customerPincode">Pincode</label>
                            <input type="text" id="customerPincode" placeholder="Enter pincode">
                        </div>
                    </div>
                    
                    <div class="form-group">
                        <label for="customerRemarks">Remarks</label>
                        <textarea id="customerRemarks" placeholder="Enter any remarks"></textarea>
                    </div>
                    
                    <button class="btn" onclick="addCustomerRecord()">Add Customer Record</button>
                </div>
                
                <h2>Customer Records</h2>
                <div class="table-container">
                    <table id="customerTable">
                        <thead>
                            <tr>
                                <th>ID</th>
                                <th>Name</th>
                                <th>Contact</th>
                                <th>Email</th>
                                <th>Address</th>
                                <th>City</th>
                                <th>State</th>
                                <th>Pincode</th>
                                <th>Status</th>
                                <th>Created At</th>
                                <th>Updated At</th>
                                <th>Remarks</th>
                                <th>Actions</th>
                            </tr>
                        </thead>
                        <tbody>
                            <!-- Customer records will be added here -->
                        </tbody>
                    </table>
                </div>
            </div>
        </div>
        
        <!-- Change Password Modal -->
        <div id="changePasswordModal" class="modal">
            <div class="modal-content">
                <div class="modal-header">
                    <h2>Change Password</h2>
                    <span class="close" onclick="closeModal('changePasswordModal')">&times;</span>
                </div>
                <div class="form-group">
                    <label for="currentPassword">Current Password</label>
                    <input type="password" id="currentPassword" placeholder="Enter current password">
                </div>
                <div class="form-group">
                    <label for="newPassword">New Password</label>
                    <input type="password" id="newPassword" placeholder="Enter new password">
                </div>
                <div class="form-group">
                    <label for="confirmPassword">Confirm New Password</label>
                    <input type="password" id="confirmPassword" placeholder="Confirm new password">
                </div>
                <button class="btn" onclick="changePassword()">Change Password</button>
            </div>
        </div>
        
        <!-- Hold Record Modal -->
        <div id="holdRecordModal" class="modal">
            <div class="modal-content">
                <div class="modal-header">
                    <h2>Put Record on Hold</h2>
                    <span class="close" onclick="closeModal('holdRecordModal')">&times;</span>
                </div>
                <div class="form-group">
                    <label for="holdRemarks">Reason for Hold</label>
                    <textarea id="holdRemarks" rows="3" placeholder="Enter reason for putting this record on hold"></textarea>
                </div>
                <button class="btn hold-btn" onclick="confirmHold()">Confirm Hold</button>
            </div>
        </div>
        
        <!-- Print Section (hidden) -->
        <div id="printSection" style="display: none;"></div>
    </div>

    <script>
        // Database using localStorage
        let machineRecords = JSON.parse(localStorage.getItem('machineRecords')) || [];
        let customerRecords = JSON.parse(localStorage.getItem('customerRecords')) || [];
        let currentUser = null;
        let currentHoldId = null;
        let currentHoldType = null;
        
        // Default admin user
        const defaultUser = {
            username: 'eraj12',
            password: '12345',
            email: 'admin@example.com'
        };
        
        // Initialize the application
        function init() {
            // Check if user is already logged in
            const loggedInUser = localStorage.getItem('loggedInUser');
            if (loggedInUser) {
                currentUser = JSON.parse(loggedInUser);
                showDashboard();
                updateStats();
                displayMachineRecords();
                displayCustomerRecords();
                loadProfile();
            }
            
            // Create default user if not exists
            if (!localStorage.getItem('users')) {
                localStorage.setItem('users', JSON.stringify([defaultUser]));
            }
        }
        
        // Login function
        function login() {
            const username = document.getElementById('username').value;
            const password = document.getElementById('password').value;
            
            const users = JSON.parse(localStorage.getItem('users'));
            const user = users.find(u => u.username === username && u.password === password);
            
            if (user) {
                currentUser = user;
                localStorage.setItem('loggedInUser', JSON.stringify(user));
                showDashboard();
                updateStats();
                displayMachineRecords();
                displayCustomerRecords();
                loadProfile();
            } else {
                alert('Invalid username or password');
            }
        }
        
        // Logout function
        function logout() {
            currentUser = null;
            localStorage.removeItem('loggedInUser');
            document.getElementById('loginSection').style.display = 'flex';
            document.getElementById('dashboard').style.display = 'none';
            document.getElementById('username').value = 'eraj12';
            document.getElementById('password').value = '12345';
        }
        
        // Show dashboard
        function showDashboard() {
            document.getElementById('loginSection').style.display = 'none';
            document.getElementById('dashboard').style.display = 'block';
            document.getElementById('displayUsername').textContent = currentUser.username;
        }
        
        // Load user profile
        function loadProfile() {
            document.getElementById('profileUsername').value = currentUser.username;
            document.getElementById('profileEmail').value = currentUser.email || '';
        }
        
        // Update user profile
        function updateProfile() {
            const newUsername = document.getElementById('profileUsername').value;
            const newEmail = document.getElementById('profileEmail').value;
            
            if (!newUsername) {
                alert('Username is required');
                return;
            }
            
            const users = JSON.parse(localStorage.getItem('users'));
            const userIndex = users.findIndex(u => u.username === currentUser.username);
            
            if (userIndex !== -1) {
                // Check if username already exists
                if (newUsername !== currentUser.username) {
                    const usernameExists = users.some(u => u.username === newUsername);
                    if (usernameExists) {
                        alert('Username already exists');
                        return;
                    }
                }
                
                users[userIndex].username = newUsername;
                users[userIndex].email = newEmail;
                localStorage.setItem('users', JSON.stringify(users));
                
                // Update current user
                currentUser.username = newUsername;
                currentUser.email = newEmail;
                localStorage.setItem('loggedInUser', JSON.stringify(currentUser));
                
                document.getElementById('displayUsername').textContent = newUsername;
                alert('Profile updated successfully');
            }
        }
        
        // Switch between tabs
        function showTab(tabName) {
            // Hide all tab contents
            document.querySelectorAll('.tab-content').forEach(tab => {
                tab.classList.remove('active');
            });
            
            // Deactivate all tab buttons
            document.querySelectorAll('.tab-btn').forEach(btn => {
                btn.classList.remove('active');
            });
            
            // Activate selected tab
            document.getElementById(tabName + 'Tab').classList.add('active');
            event.target.classList.add('active');
        }
        
        // Add new machine record
        function addMachineRecord() {
            const machineName = document.getElementById('machineName').value;
            const serialNumber = document.getElementById('serialNumber').value;
            const photoInput = document.getElementById('machinePhoto');
            const recordType = document.getElementById('machineType').value;
            const remarks = document.getElementById('machineRemarks').value;
            
            if (!machineName || !serialNumber) {
                alert('Machine name and serial number are required');
                return;
            }
            
            let photo = null;
            if (photoInput.files.length > 0) {
                const file = photoInput.files[0];
                photo = URL.createObjectURL(file);
            }
            
            const newRecord = {
                id: Date.now(),
                machineName,
                serialNumber,
                photo,
                recordType,
                status: 'Pending',
                createdAt: new Date().toLocaleString(),
                updatedAt: new Date().toLocaleString(),
                remarks,
                updatedBy: currentUser.username
            };
            
            machineRecords.push(newRecord);
            saveRecords();
            
            // Clear form
            document.getElementById('machineName').value = '';
            document.getElementById('serialNumber').value = '';
            document.getElementById('machinePhoto').value = '';
            document.getElementById('machineRemarks').value = '';
            
            updateStats();
            displayMachineRecords();
        }
        
        // Add new customer record
        function addCustomerRecord() {
            const firstName = document.getElementById('customerFirstName').value;
            const lastName = document.getElementById('customerLastName').value;
            const contact = document.getElementById('customerContact').value;
            const email = document.getElementById('customerEmail').value;
            const address = document.getElementById('customerAddress').value;
            const city = document.getElementById('customerCity').value;
            const state = document.getElementById('customerState').value;
            const pincode = document.getElementById('customerPincode').value;
            const remarks = document.getElementById('customerRemarks').value;
            
            if (!firstName || !contact) {
                alert('First name and contact number are required');
                return;
            }
            
            const newRecord = {
                id: Date.now(),
                firstName,
                lastName,
                contact,
                email,
                address,
                city,
                state,
                pincode,
                status: 'Pending',
                createdAt: new Date().toLocaleString(),
                updatedAt: new Date().toLocaleString(),
                remarks,
                updatedBy: currentUser.username
            };
            
            customerRecords.push(newRecord);
            saveRecords();
            
            // Clear form
            document.getElementById('customerFirstName').value = '';
            document.getElementById('customerLastName').value = '';
            document.getElementById('customerContact').value = '';
            document.getElementById('customerEmail').value = '';
            document.getElementById('customerAddress').value = '';
            document.getElementById('customerCity').value = '';
            document.getElementById('customerState').value = '';
            document.getElementById('customerPincode').value = '';
            document.getElementById('customerRemarks').value = '';
            
            updateStats();
            displayCustomerRecords();
        }
        
        // Update record status
        function updateRecordStatus(id, type, status, remarks = '') {
            let records = type === 'machine' ? machineRecords : customerRecords;
            const record = records.find(r => r.id === id);
            
            if (record) {
                record.status = status;
                record.updatedAt = new Date().toLocaleString();
                record.updatedBy = currentUser.username;
                if (remarks) {
                    record.remarks = remarks;
                }
                saveRecords();
                updateStats();
                
                if (type === 'machine') {
                    displayMachineRecords();
                } else {
                    displayCustomerRecords();
                }
            }
        }
        
        // Delete record
        function deleteRecord(id, type) {
            if (confirm('Are you sure you want to delete this record?')) {
                if (type === 'machine') {
                    machineRecords = machineRecords.filter(r => r.id !== id);
                } else {
                    customerRecords = customerRecords.filter(r => r.id !== id);
                }
                saveRecords();
                updateStats();
                
                if (type === 'machine') {
                    displayMachineRecords();
                } else {
                    displayCustomerRecords();
                }
            }
        }
        
        // Show hold record modal
        function showHoldModal(id, type) {
            currentHoldId = id;
            currentHoldType = type;
            document.getElementById('holdRemarks').value = '';
            document.getElementById('holdRecordModal').style.display = 'flex';
        }
        
        // Confirm hold
        function confirmHold() {
            const remarks = document.getElementById('holdRemarks').value;
            if (!remarks) {
                alert('Please enter a reason for hold');
                return;
            }
            
            updateRecordStatus(currentHoldId, currentHoldType, 'Hold', remarks);
            closeModal('holdRecordModal');
        }
        
        // Print record
        function printRecord(id, type) {
            const printSection = document.getElementById('printSection');
            printSection.innerHTML = '';
            
            let record, title;
            if (type === 'machine') {
                record = machineRecords.find(r => r.id === id);
                title = 'Machine Record Details';
            } else {
                record = customerRecords.find(r => r.id === id);
                title = 'Customer Record Details';
            }
            
            if (!record) return;
            
            let content = `
                <div style="padding: 20px;">
                    <h1 style="text-align: center; color: #4CAF50; margin-bottom: 20px;">${title}</h1>
                    <div style="border: 1px solid #ddd; padding: 20px; border-radius: 8px;">
            `;
            
            if (type === 'machine') {
                content += `
                    <p><strong>ID:</strong> ${record.id}</p>
                    <p><strong>Machine Name:</strong> ${record.machineName}</p>
                    <p><strong>Serial Number:</strong> ${record.serialNumber}</p>
                    <p><strong>Type:</strong> ${record.recordType}</p>
                    <p><strong>Status:</strong> ${record.status}</p>
                    <p><strong>Created At:</strong> ${record.createdAt}</p>
                    <p><strong>Updated At:</strong> ${record.updatedAt}</p>
                    <p><strong>Updated By:</strong> ${record.updatedBy}</p>
                    <p><strong>Remarks:</strong> ${record.remarks || '-'}</p>
                `;
            } else {
                content += `
                    <p><strong>ID:</strong> ${record.id}</p>
                    <p><strong>Name:</strong> ${record.firstName} ${record.lastName}</p>
                    <p><strong>Contact:</strong> ${record.contact}</p>
                    <p><strong>Email:</strong> ${record.email || '-'}</p>
                    <p><strong>Address:</strong> ${record.address}</p>
                    <p><strong>City:</strong> ${record.city}</p>
                    <p><strong>State:</strong> ${record.state}</p>
                    <p><strong>Pincode:</strong> ${record.pincode}</p>
                    <p><strong>Status:</strong> ${record.status}</p>
                    <p><strong>Created At:</strong> ${record.createdAt}</p>
                    <p><strong>Updated At:</strong> ${record.updatedAt}</p>
                    <p><strong>Updated By:</strong> ${record.updatedBy}</p>
                    <p><strong>Remarks:</strong> ${record.remarks || '-'}</p>
                `;
            }
            
            content += `
                    </div>
                    <p style="text-align: right; margin-top: 20px; font-style: italic;">
                        Printed on ${new Date().toLocaleString()}
                    </p>
                </div>
            `;
            
            printSection.innerHTML = content;
            window.print();
        }
        
        // Show change password modal
        function showChangePasswordModal() {
            document.getElementById('currentPassword').value = '';
            document.getElementById('newPassword').value = '';
            document.getElementById('confirmPassword').value = '';
            document.getElementById('changePasswordModal').style.display = 'flex';
        }
        
        // Change password
        function changePassword() {
            const currentPassword = document.getElementById('currentPassword').value;
            const newPassword = document.getElementById('newPassword').value;
            const confirmPassword = document.getElementById('confirmPassword').value;
            
            if (currentPassword !== currentUser.password) {
                alert('Current password is incorrect');
                return;
            }
            
            if (newPassword !== confirmPassword) {
                alert('New passwords do not match');
                return;
            }
            
            const users = JSON.parse(localStorage.getItem('users'));
            const userIndex = users.findIndex(u => u.username === currentUser.username);
            
            if (userIndex !== -1) {
                users[userIndex].password = newPassword;
                localStorage.setItem('users', JSON.stringify(users));
                
                // Update current user
                currentUser.password = newPassword;
                localStorage.setItem('loggedInUser', JSON.stringify(currentUser));
                
                alert('Password changed successfully');
                closeModal('changePasswordModal');
            }
        }
        
        // Close modal
        function closeModal(modalId) {
            document.getElementById(modalId).style.display = 'none';
        }
        
        // Save records to localStorage
        function saveRecords() {
            localStorage.setItem('machineRecords', JSON.stringify(machineRecords));
            localStorage.setItem('customerRecords', JSON.stringify(customerRecords));
        }
        
        // Update statistics
        function updateStats() {
            const totalRecords = machineRecords.length + customerRecords.length;
            const acceptedRecords = 
                machineRecords.filter(r => r.status === 'Accepted').length + 
                customerRecords.filter(r => r.status === 'Accepted').length;
            const holdRecords = 
                machineRecords.filter(r => r.status === 'Hold').length + 
                customerRecords.filter(r => r.status === 'Hold').length;
            
            document.getElementById('totalRecords').textContent = totalRecords;
            document.getElementById('acceptedRecords').textContent = acceptedRecords;
            document.getElementById('holdRecords').textContent = holdRecords;
        }
        
        // Display machine records in table
        function displayMachineRecords() {
            const tbody = document.querySelector('#machineTable tbody');
            tbody.innerHTML = '';
            
            machineRecords.forEach(record => {
                const row = document.createElement('tr');
                
                row.innerHTML = `
                    <td>${record.id}</td>
                    <td>${record.machineName}</td>
                    <td>${record.serialNumber}</td>
                    <td>${record.photo ? `<img src="${record.photo}" class="photo-preview">` : 'No photo'}</td>
                    <td>${record.recordType}</td>
                    <td>${record.status}</td>
                    <td>${record.createdAt}</td>
                    <td>${record.updatedAt}</td>
                    <td>${record.remarks || '-'}</td>
                    <td>
                        ${record.status !== 'Accepted' ? `<button class="action-btn accept-btn" onclick="updateRecordStatus(${record.id}, 'machine', 'Accepted')">Accept</button>` : ''}
                        ${record.status !== 'Hold' ? `<button class="action-btn hold-btn" onclick="showHoldModal(${record.id}, 'machine')">Hold</button>` : ''}
                        <button class="action-btn print-btn" onclick="printRecord(${record.id}, 'machine')">Print</button>
                        <button class="action-btn delete-btn" onclick="deleteRecord(${record.id}, 'machine')">Delete</button>
                    </td>
                `;
                
                tbody.appendChild(row);
            });
        }
        
        // Display customer records in table
        function displayCustomerRecords() {
            const tbody = document.querySelector('#customerTable tbody');
            tbody.innerHTML = '';
            
            customerRecords.forEach(record => {
                const row = document.createElement('tr');
                
                row.innerHTML = `
                    <td>${record.id}</td>
                    <td>${record.firstName} ${record.lastName}</td>
                    <td>${record.contact}</td>
                    <td>${record.email || '-'}</td>
                    <td>${record.address}</td>
                    <td>${record.city}</td>
                    <td>${record.state}</td>
                    <td>${record.pincode}</td>
                    <td>${record.status}</td>
                    <td>${record.createdAt}</td>
                    <td>${record.updatedAt}</td>
                    <td>${record.remarks || '-'}</td>
                    <td>
                        ${record.status !== 'Accepted' ? `<button class="action-btn accept-btn" onclick="updateRecordStatus(${record.id}, 'customer', 'Accepted')">Accept</button>` : ''}
                        ${record.status !== 'Hold' ? `<button class="action-btn hold-btn" onclick="showHoldModal(${record.id}, 'customer')">Hold</button>` : ''}
                        <button class="action-btn print-btn" onclick="printRecord(${record.id}, 'customer')">Print</button>
                        <button class="action-btn delete-btn" onclick="deleteRecord(${record.id}, 'customer')">Delete</button>
                    </td>
                `;
                
                tbody.appendChild(row);
            });
        }
        
        // Initialize the app when page loads
        window.onload = init;
    </script>
</body>
</html>
