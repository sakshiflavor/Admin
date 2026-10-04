<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Chaat Puchka - Global Admin Dashboard</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
</head>
<body class="bg-amber-50/50 text-slate-800 font-sans">
    <div class="max-w-6xl mx-auto p-4 sm:p-6">
        <!-- Header -->
        <div class="flex flex-col sm:flex-row justify-between items-center gap-4 mb-6 bg-white p-5 rounded-2xl shadow-sm border border-amber-100">
            <div class="flex items-center space-x-3 w-full sm:w-auto">
                <div class="w-12 h-12 flex-shrink-0 bg-black/80 rounded-xl p-1 shadow-md flex items-center justify-center">
                    <img src="https://i.postimg.cc/SsSZBQ9q/1000037254-removebg-preview.png" alt="Chaat Puchka Logo" class="w-full h-full object-contain">
                </div>
                <div>
                    <h2 class="text-xl sm:text-2xl font-black tracking-tight text-slate-900">Chaat Puchka <span class="text-amber-600 text-xs sm:text-sm font-semibold uppercase block tracking-normal">Global Admin Dashboard</span></h2>
                </div>
            </div>
            <button onclick="window.location.href='index.html';" class="bg-red-500 hover:bg-red-600 text-white px-4 py-2 rounded-xl text-sm font-semibold shadow transition w-full sm:w-auto">Logout</button>
        </div>

        <!-- Global Metrics Overview -->
        <div class="grid grid-cols-1 sm:grid-cols-3 gap-4 sm:gap-6 mb-8">
            <div class="bg-white p-6 rounded-2xl shadow-sm border border-amber-100">
                <p class="text-xs text-amber-600 uppercase font-bold tracking-wider">Total Global Revenue</p>
                <h3 id="global-revenue" class="text-3xl font-black text-slate-900 mt-2">₹0</h3>
            </div>
            <div class="bg-white p-6 rounded-2xl shadow-sm border border-amber-100">
                <p class="text-xs text-amber-600 uppercase font-bold tracking-wider">Total Global Orders</p>
                <h3 id="global-orders-count" class="text-3xl font-black text-slate-900 mt-2">0</h3>
            </div>
            <div class="bg-white p-6 rounded-2xl shadow-sm border border-amber-100">
                <p class="text-xs text-amber-600 uppercase font-bold tracking-wider">Active Puchka Outlets</p>
                <h3 id="active-branches-count" class="text-3xl font-black text-emerald-600 mt-2">0</h3>
            </div>
        </div>

        <!-- Add/Edit Branch Form -->
        <div class="bg-white p-6 rounded-2xl shadow-sm border border-amber-100 mb-8">
            <h3 class="text-lg font-bold mb-4 flex items-center text-slate-900"><i class="fa-solid fa-store text-amber-500 mr-2"></i> Franchise Branch Management</h3>
            <input type="hidden" id="editBranchKey" value="">
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4 mb-4">
                <input type="text" id="branchNameInput" placeholder="Branch Name (e.g. MG Road Puchka Stall)" class="border border-slate-200 rounded-xl p-3 text-sm focus:outline-none focus:ring-2 focus:ring-amber-500">
                <input type="text" id="branchLoginId" placeholder="Branch Login ID" class="border border-slate-200 rounded-xl p-3 text-sm focus:outline-none focus:ring-2 focus:ring-amber-500">
                <input type="password" id="branchPassword" placeholder="Branch Password" class="border border-slate-200 rounded-xl p-3 text-sm focus:outline-none focus:ring-2 focus:ring-amber-500">
                <input type="number" step="any" id="branchLat" placeholder="Latitude (e.g. 12.9716)" class="border border-slate-200 rounded-xl p-3 text-sm focus:outline-none focus:ring-2 focus:ring-amber-500">
                <input type="number" step="any" id="branchLng" placeholder="Longitude (e.g. 77.5946)" class="border border-slate-200 rounded-xl p-3 text-sm focus:outline-none focus:ring-2 focus:ring-amber-500">
            </div>
            <button onclick="saveBranch()" id="branchSaveBtn" class="bg-emerald-500 hover:bg-emerald-600 text-white font-extrabold py-3 px-6 rounded-xl text-sm shadow transition w-full sm:w-auto">Add Franchise Branch</button>
        </div>

        <!-- Branches Table -->
        <div class="bg-white rounded-2xl shadow-sm border border-amber-100 overflow-x-auto">
            <div class="p-4 bg-amber-50 font-bold text-amber-900 text-xs uppercase tracking-wider">Configured Franchise Branches</div>
            <table class="w-full text-left border-collapse min-w-[600px]">
                <thead class="bg-slate-50 text-slate-600 text-xs uppercase">
                    <tr>
                        <th class="p-4">Branch Name</th>
                        <th class="p-4">Login ID</th>
                        <th class="p-4">Coordinates (Lat, Lng)</th>
                        <th class="p-4 text-right">Actions</th>
                    </tr>
                </thead>
                <tbody id="branchesTableBody" class="divide-y divide-slate-100 text-sm">
                    <tr><td colspan="4" class="p-4 text-center text-slate-400">Loading branches...</td></tr>
                </tbody>
            </table>
        </div>
    </div>

    <script type="module">
        import { initializeApp } from "https://www.gstatic.com/firebasejs/10.8.0/firebase-app.js";
        import { getDatabase, ref, onValue, push, update, remove } from "https://www.gstatic.com/firebasejs/10.8.0/firebase-database.js";

        const firebaseConfig = {
            databaseURL: "https://teat-2-4b868-default-rtdb.europe-west1.firebasedatabase.app/"
        };
        const app = initializeApp(firebaseConfig);
        const db = getDatabase(app);

        onValue(ref(db, 'franchises'), (snapshot) => {
            const data = snapshot.val();
            const tableBody = document.getElementById('branchesTableBody');
            tableBody.innerHTML = '';
            
            if (!data) {
                tableBody.innerHTML = '<tr><td colspan="4" class="p-4 text-center text-slate-400">No branches configured yet.</td></tr>';
                document.getElementById('active-branches-count').innerText = 0;
                return;
            }

            let branchCount = 0;
            Object.entries(data).forEach(([key, branch]) => {
                branchCount++;
                tableBody.innerHTML += `
                    <tr>
                        <td class="p-4 font-semibold text-slate-900"><i class="fa-solid fa-shop text-amber-500 mr-2"></i>${branch.name}</td>
                        <td class="p-4 text-slate-600 font-mono">${branch.loginId}</td>
                        <td class="p-4 text-slate-500 text-xs">${branch.lat}, ${branch.lng}</td>
                        <td class="p-4 text-right space-x-2">
                            <button onclick="window.editBranch('${key}', '${branch.name}', '${branch.loginId}', '${branch.password}', ${branch.lat}, ${branch.lng})" class="text-blue-600 hover:text-blue-800"><i class="fa-solid fa-pen"></i></button>
                            <button onclick="window.deleteBranch('${key}')" class="text-red-500 hover:text-red-700"><i class="fa-solid fa-trash"></i></button>
                        </td>
                    </tr>`;
            });
            document.getElementById('active-branches-count').innerText = branchCount;
        });

        onValue(ref(db, 'orders'), (snapshot) => {
            const allOrdersData = snapshot.val();
            let totalRevenue = 0;
            let totalOrders = 0;

            if (allOrdersData) {
                Object.values(allOrdersData).forEach(branchOrders => {
                    if (branchOrders) {
                        Object.values(branchOrders).forEach(order => {
                            totalOrders++;
                            if (order.items) {
                                order.items.forEach(item => {
                                    totalRevenue += (item.price * (item.qty || 1));
                                });
                            }
                        });
                    }
                });
            }

            document.getElementById('global-revenue').innerText = `₹${totalRevenue}`;
            document.getElementById('global-orders-count').innerText = totalOrders;
        });

        window.saveBranch = function() {
            const editKey = document.getElementById('editBranchKey').value;
            const name = document.getElementById('branchNameInput').value.trim();
            const loginId = document.getElementById('branchLoginId').value.trim();
            const password = document.getElementById('branchPassword').value.trim();
            const lat = parseFloat(document.getElementById('branchLat').value);
            const lng = parseFloat(document.getElementById('branchLng').value);

            if (!name || !loginId || !password || isNaN(lat) || isNaN(lng)) {
                alert('Please fill out all branch fields correctly with valid numbers for coordinates.');
                return;
            }

            const branchData = { name, loginId, password, lat, lng };

            if (editKey) {
                update(ref(db, `franchises/${editKey}`), branchData).then(() => {
                    resetForm();
                    alert('Branch updated successfully!');
                });
            } else {
                push(ref(db, 'franchises'), branchData).then(() => {
                    resetForm();
                    alert('Branch added successfully!');
                });
            }
        };

        window.editBranch = function(key, name, loginId, password, lat, lng) {
            document.getElementById('editBranchKey').value = key;
            document.getElementById('branchNameInput').value = name;
            document.getElementById('branchLoginId').value = loginId;
            document.getElementById('branchPassword').value = password;
            document.getElementById('branchLat').value = lat;
            document.getElementById('branchLng').value = lng;
            document.getElementById('branchSaveBtn').innerText = "Update Branch";
        };

        window.deleteBranch = function(key) {
            if (confirm('Are you sure you want to delete this franchise branch?')) {
                remove(ref(db, `franchises/${key}`)).then(() => {
                    alert('Branch deleted successfully.');
                });
            }
        };

        function resetForm() {
            document.getElementById('editBranchKey').value = '';
            document.getElementById('branchNameInput').value = '';
            document.getElementById('branchLoginId').value = '';
            document.getElementById('branchPassword').value = '';
            document.getElementById('branchLat').value = '';
            document.getElementById('branchLng').value = '';
            document.getElementById('branchSaveBtn').innerText = "Add Franchise Branch";
        }
    </script>
</body>
</html>
