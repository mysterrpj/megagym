<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MEGAGYM - Sistema de Gestión</title>
    <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;500;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <style>
        :root {
            --primary-color: #FF3B30;
            --secondary-color: #333;
            --light-color: #f8f9fa;
            --border-color: #e9ecef;
            --success-color: #28a745;
            --danger-color: #dc3545;
            --info-color: #17a2b8;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Roboto', sans-serif;
            background-color: var(--light-color);
            color: var(--secondary-color);
            line-height: 1.6;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }
        
        header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 20px 0;
            border-bottom: 1px solid var(--border-color);
            margin-bottom: 30px;
        }
        
        .logo {
            font-size: 2rem;
            font-weight: 700;
            color: var(--primary-color);
            letter-spacing: 1px;
        }
        
        .stats {
            display: flex;
            gap: 20px;
        }
        
        .stat-card {
            background: white;
            border-radius: 8px;
            padding: 15px 20px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.05);
            text-align: center;
            min-width: 120px;
        }
        
        .stat-value {
            font-size: 1.8rem;
            font-weight: 700;
            color: var(--primary-color);
        }
        
        .stat-label {
            font-size: 0.9rem;
            color: #6c757d;
        }
        
        .card {
            background: white;
            border-radius: 8px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.05);
            margin-bottom: 30px;
            overflow: hidden;
        }
        
        .card-header {
            padding: 15px 20px;
            border-bottom: 1px solid var(--border-color);
            font-weight: 700;
            font-size: 1.1rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .card-body {
            padding: 20px;
        }
        
        .form-group {
            margin-bottom: 15px;
        }
        
        label {
            display: block;
            margin-bottom: 5px;
            font-weight: 500;
        }
        
        input, select {
            width: 100%;
            padding: 10px;
            border: 1px solid var(--border-color);
            border-radius: 4px;
            font-family: inherit;
        }
        
        .btn {
            padding: 10px 20px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-weight: 500;
            transition: all 0.3s ease;
            display: inline-flex;
            align-items: center;
            gap: 8px;
        }
        
        .btn-primary {
            background-color: var(--primary-color);
            color: white;
        }
        
        .btn-primary:hover {
            background-color: #e02c21;
        }
        
        .btn-secondary {
            background-color: #6c757d;
            color: white;
        }
        
        .btn-success {
            background-color: var(--success-color);
            color: white;
        }
        
        .btn-danger {
            background-color: var(--danger-color);
            color: white;
        }
        
        .btn-info {
            background-color: var(--info-color);
            color: white;
        }
        
        .btn-sm {
            padding: 5px 10px;
            font-size: 0.875rem;
        }
        
        .table {
            width: 100%;
            border-collapse: collapse;
        }
        
        .table th, .table td {
            padding: 12px 15px;
            text-align: left;
            border-bottom: 1px solid var(--border-color);
        }
        
        .table th {
            font-weight: 600;
            background-color: #f8f9fa;
        }
        
        .table tbody tr:hover {
            background-color: #f8f9fa;
        }
        
        .status-active {
            color: var(--success-color);
            font-weight: 500;
        }
        
        .status-inactive {
            color: var(--danger-color);
            font-weight: 500;
        }
        
        .filter-container {
            display: flex;
            gap: 15px;
            margin-bottom: 20px;
        }
        
        .filter-container .form-group {
            flex: 1;
            margin-bottom: 0;
        }
        
        .actions {
            display: flex;
            gap: 10px;
        }
        
        .notification {
            position: fixed;
            top: 20px;
            right: 20px;
            padding: 15px 20px;
            background-color: var(--success-color);
            color: white;
            border-radius: 4px;
            box-shadow: 0 3px 10px rgba(0,0,0,0.2);
            transform: translateX(200%);
            transition: transform 0.3s ease;
            z-index: 1000;
            display: flex;
            align-items: center;
            gap: 10px;
            max-width: 350px;
        }
        
        .notification.show {
            transform: translateX(0);
        }
        
        .notification.error {
            background-color: var(--danger-color);
        }
        
        .form-row {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 15px;
        }
        
        .empty-state {
            text-align: center;
            padding: 40px 20px;
            color: #6c757d;
        }
        
        .empty-state i {
            font-size: 3rem;
            margin-bottom: 15px;
            color: #dee2e6;
        }
        
        .price-display {
            margin-top: 5px;
            font-weight: 500;
            color: var(--primary-color);
        }
        
        .price-config-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 15px;
        }
        
        .price-input-group {
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .price-input-group input {
            flex: 1;
        }
        
        .price-input-group span {
            font-weight: 500;
        }
        
        .tab-container {
            display: flex;
            border-bottom: 1px solid var(--border-color);
            margin-bottom: 20px;
        }
        
        .tab {
            padding: 10px 20px;
            cursor: pointer;
            border-bottom: 2px solid transparent;
            font-weight: 500;
            transition: all 0.3s;
        }
        
        .tab:hover {
            color: var(--primary-color);
        }
        
        .tab.active {
            color: var(--primary-color);
            border-bottom-color: var(--primary-color);
        }
        
        .tab-content {
            display: none;
        }
        
        .tab-content.active {
            display: block;
        }
        
        @media (max-width: 768px) {
            .stats {
                flex-direction: column;
                gap: 10px;
            }
            
            .filter-container {
                flex-direction: column;
            }
            
            .actions {
                flex-direction: column;
            }
            
            .table {
                font-size: 0.9rem;
            }
            
            .table th, .table td {
                padding: 8px 10px;
            }
            
            .form-row {
                grid-template-columns: 1fr;
            }
            
            .tab-container {
                overflow-x: auto;
                white-space: nowrap;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <div class="logo">MEGAGYM</div>
            <div class="stats">
                <div class="stat-card">
                    <div class="stat-value" id="totalClients">0</div>
                    <div class="stat-label">Total Clientes</div>
                </div>
                <div class="stat-card">
                    <div class="stat-value" id="activeClients">0</div>
                    <div class="stat-label">Activos</div>
                </div>
                <div class="stat-card">
                    <div class="stat-value" id="inactiveClients">0</div>
                    <div class="stat-label">Inactivos</div>
                </div>
            </div>
        </header>
        
        <div class="tab-container">
            <div class="tab active" data-tab="clients">
                <i class="fas fa-users"></i> Clientes
            </div>
            <div class="tab" data-tab="prices">
                <i class="fas fa-tags"></i> Precios de Membresías
            </div>
        </div>
        
        <div id="clients-tab" class="tab-content active">
            <div class="card">
                <div class="card-header">
                    <span><i class="fas fa-user-plus"></i> Registrar Nuevo Cliente</span>
                    <span id="formMode" style="font-size: 0.9rem; color: #6c757d;"></span>
                </div>
                <div class="card-body">
                    <form id="clientForm">
                        <div class="form-row">
                            <div class="form-group">
                                <label for="name">Nombre</label>
                                <input type="text" id="name" required>
                            </div>
                            <div class="form-group">
                                <label for="lastName">Apellido</label>
                                <input type="text" id="lastName" required>
                            </div>
                        </div>
                        <div class="form-row">
                            <div class="form-group">
                                <label for="phone">Teléfono</label>
                                <input type="tel" id="phone" required>
                            </div>
                            <div class="form-group">
                                <label for="email">Email</label>
                                <input type="email" id="email">
                            </div>
                        </div>
                        <div class="form-row">
                            <div class="form-group">
                                <label for="membership">Tipo de Membresía</label>
                                <select id="membership" required>
                                    <option value="">Seleccionar...</option>
                                    <option value="Mensual">Mensual</option>
                                    <option value="Trimestral">Trimestral</option>
                                    <option value="Semestral">Semestral</option>
                                    <option value="Anual">Anual</option>
                                </select>
                                <div id="membershipPrice" class="price-display"></div>
                            </div>
                            <div class="form-group">
                                <label for="startDate">Fecha de Inicio</label>
                                <input type="date" id="startDate" required>
                            </div>
                        </div>
                        <div style="margin-top: 20px;">
                            <button type="submit" class="btn btn-primary" id="submitBtn">
                                <i class="fas fa-save"></i> Registrar Cliente
                            </button>
                            <button type="button" class="btn btn-secondary" id="cancelEditBtn" style="display: none;">
                                <i class="fas fa-times"></i> Cancelar
                            </button>
                        </div>
                    </form>
                </div>
            </div>
            
            <div class="card">
                <div class="card-header">
                    <span><i class="fas fa-list"></i> Gestión de Clientes</span>
                </div>
                <div class="card-body">
                    <div class="filter-container">
                        <div class="form-group">
                            <input type="text" id="searchInput" placeholder="Buscar por nombre, apellido o email...">
                        </div>
                        <div class="form-group">
                            <select id="statusFilter">
                                <option value="">Todos los estados</option>
                                <option value="active">Activos</option>
                                <option value="inactive">Inactivos</option>
                            </select>
                        </div>
                        <div class="form-group">
                            <button id="clearFilters" class="btn btn-primary">
                                <i class="fas fa-times"></i> Limpiar Filtros
                            </button>
                        </div>
                    </div>
                    
                    <div style="overflow-x: auto;">
                        <table class="table">
                            <thead>
                                <tr>
                                    <th>ID</th>
                                    <th>Nombre</th>
                                    <th>Teléfono</th>
                                    <th>Email</th>
                                    <th>Membresía</th>
                                    <th>Precio</th>
                                    <th>Inicio</th>
                                    <th>Fin</th>
                                    <th>Estado</th>
                                    <th>Acciones</th>
                                </tr>
                            </thead>
                            <tbody id="clientsTableBody">
                                <!-- Los clientes se cargarán aquí dinámicamente -->
                            </tbody>
                        </table>
                        <div id="emptyState" class="empty-state" style="display: none;">
                            <i class="fas fa-users"></i>
                            <p>No hay clientes registrados</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        
        <div id="prices-tab" class="tab-content">
            <div class="card">
                <div class="card-header">
                    <span><i class="fas fa-cog"></i> Configuración de Precios</span>
                </div>
                <div class="card-body">
                    <form id="pricesForm">
                        <div class="price-config-grid">
                            <div class="form-group">
                                <label for="priceMensual">Mensual</label>
                                <div class="price-input-group">
                                    <span>$</span>
                                    <input type="number" id="priceMensual" min="0" step="0.01" required>
                                </div>
                            </div>
                            <div class="form-group">
                                <label for="priceTrimestral">Trimestral</label>
                                <div class="price-input-group">
                                    <span>$</span>
                                    <input type="number" id="priceTrimestral" min="0" step="0.01" required>
                                </div>
                            </div>
                            <div class="form-group">
                                <label for="priceSemestral">Semestral</label>
                                <div class="price-input-group">
                                    <span>$</span>
                                    <input type="number" id="priceSemestral" min="0" step="0.01" required>
                                </div>
                            </div>
                            <div class="form-group">
                                <label for="priceAnual">Anual</label>
                                <div class="price-input-group">
                                    <span>$</span>
                                    <input type="number" id="priceAnual" min="0" step="0.01" required>
                                </div>
                            </div>
                        </div>
                        <div style="margin-top: 20px;">
                            <button type="submit" class="btn btn-success">
                                <i class="fas fa-save"></i> Guardar Precios
                            </button>
                        </div>
                    </form>
                </div>
            </div>
            
            <div class="card">
                <div class="card-header">
                    <span><i class="fas fa-chart-bar"></i> Resumen de Precios</span>
                </div>
                <div class="card-body">
                    <div class="price-config-grid">
                        <div class="stat-card">
                            <div class="stat-value" id="summaryMensual">$0</div>
                            <div class="stat-label">Mensual</div>
                        </div>
                        <div class="stat-card">
                            <div class="stat-value" id="summaryTrimestral">$0</div>
                            <div class="stat-label">Trimestral</div>
                        </div>
                        <div class="stat-card">
                            <div class="stat-value" id="summarySemestral">$0</div>
                            <div class="stat-label">Semestral</div>
                        </div>
                        <div class="stat-card">
                            <div class="stat-value" id="summaryAnual">$0</div>
                            <div class="stat-label">Anual</div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
    
    <div id="notification" class="notification">
        <i class="fas fa-check-circle"></i>
        <span></span>
    </div>
    
    <script>
        document.addEventListener('DOMContentLoaded', function() {
            // Inicializar datos
            let clients = [];
            let membershipPrices = {
                'Mensual': 30.00,
                'Trimestral': 80.00,
                'Semestral': 150.00,
                'Anual': 280.00
            };
            let db;
            let editingClientId = null;
            
            // Elementos del DOM
            const clientForm = document.getElementById('clientForm');
            const pricesForm = document.getElementById('pricesForm');
            const clientsTableBody = document.getElementById('clientsTableBody');
            const searchInput = document.getElementById('searchInput');
            const statusFilter = document.getElementById('statusFilter');
            const clearFiltersBtn = document.getElementById('clearFilters');
            const notification = document.getElementById('notification');
            const emptyState = document.getElementById('emptyState');
            const submitBtn = document.getElementById('submitBtn');
            const cancelEditBtn = document.getElementById('cancelEditBtn');
            const formMode = document.getElementById('formMode');
            const membershipSelect = document.getElementById('membership');
            const membershipPriceDisplay = document.getElementById('membershipPrice');
            
            // Tabs
            const tabs = document.querySelectorAll('.tab');
            const tabContents = document.querySelectorAll('.tab-content');
            
            // Event listeners para tabs
            tabs.forEach(tab => {
                tab.addEventListener('click', () => {
                    const tabId = tab.getAttribute('data-tab');
                    
                    tabs.forEach(t => t.classList.remove('active'));
                    tabContents.forEach(tc => tc.classList.remove('active'));
                    
                    tab.classList.add('active');
                    document.getElementById(`${tabId}-tab`).classList.add('active');
                });
            });
            
            // Mostrar notificación
            function showNotification(message, isError = false) {
                const notificationText = notification.querySelector('span');
                const notificationIcon = notification.querySelector('i');
                
                notificationText.textContent = message;
                notification.classList.add('show');
                
                if (isError) {
                    notification.classList.add('error');
                    notificationIcon.className = 'fas fa-exclamation-circle';
                } else {
                    notification.classList.remove('error');
                    notificationIcon.className = 'fas fa-check-circle';
                }
                
                setTimeout(() => {
                    notification.classList.remove('show');
                }, 3000);
            }
            
            // Inicializar IndexedDB
            function initIndexedDB() {
                const request = indexedDB.open('MegagymDB', 2);
                
                request.onerror = function(event) {
                    console.error('Error al abrir IndexedDB:', event.target.error);
                    showNotification('Error al inicializar la base de datos', true);
                };
                
                request.onsuccess = function(event) {
                    db = event.target.result;
                    console.log('IndexedDB inicializada correctamente');
                    loadClientsFromDB();
                    loadPricesFromDB();
                };
                
                request.onupgradeneeded = function(event) {
                    db = event.target.result;
                    
                    // Crear almacén de objetos para clientes
                    if (!db.objectStoreNames.contains('clients')) {
                        const clientStore = db.createObjectStore('clients', { keyPath: 'id', autoIncrement: true });
                        
                        // Crear índices para búsquedas
                        clientStore.createIndex('name', 'name', { unique: false });
                        clientStore.createIndex('lastName', 'lastName', { unique: false });
                        clientStore.createIndex('phone', 'phone', { unique: false });
                        clientStore.createIndex('email', 'email', { unique: false });
                        clientStore.createIndex('membership', 'membership', { unique: false });
                        clientStore.createIndex('status', 'status', { unique: false });
                    }
                    
                    // Crear almacén de objetos para precios de membresías
                    if (!db.objectStoreNames.contains('prices')) {
                        const priceStore = db.createObjectStore('prices', { keyPath: 'membership' });
                    }
                    
                    console.log('Estructura de IndexedDB creada');
                };
            }
            
            // Cargar clientes desde IndexedDB
            function loadClientsFromDB() {
                if (!db) {
                    console.error('Base de datos no inicializada');
                    return;
                }
                
                const transaction = db.transaction(['clients'], 'readonly');
                const objectStore = transaction.objectStore('clients');
                const request = objectStore.getAll();
                
                request.onsuccess = function(event) {
                    clients = event.target.result;
                    renderClients();
                    updateStats();
                    console.log('Clientes cargados desde IndexedDB:', clients);
                };
                
                request.onerror = function(event) {
                    console.error('Error al cargar clientes:', event.target.error);
                    showNotification('Error al cargar los clientes', true);
                };
            }
            
            // Cargar precios desde IndexedDB
            function loadPricesFromDB() {
                if (!db) {
                    console.error('Base de datos no inicializada');
                    return;
                }
                
                const transaction = db.transaction(['prices'], 'readonly');
                const objectStore = transaction.objectStore('prices');
                const request = objectStore.getAll();
                
                request.onsuccess = function(event) {
                    const prices = event.target.result;
                    
                    // Actualizar precios por defecto con los de la base de datos
                    prices.forEach(price => {
                        membershipPrices[price.membership] = price.price;
                    });
                    
                    // Actualizar formulario de precios
                    document.getElementById('priceMensual').value = membershipPrices['Mensual'];
                    document.getElementById('priceTrimestral').value = membershipPrices['Trimestral'];
                    document.getElementById('priceSemestral').value = membershipPrices['Semestral'];
                    document.getElementById('priceAnual').value = membershipPrices['Anual'];
                    
                    // Actualizar resumen de precios
                    updatePriceSummary();
                    
                    console.log('Precios cargados desde IndexedDB:', membershipPrices);
                };
                
                request.onerror = function(event) {
                    console.error('Error al cargar precios:', event.target.error);
                    showNotification('Error al cargar los precios', true);
                };
            }
            
            // Guardar precios en IndexedDB
            function savePricesToDB() {
                if (!db) {
                    console.error('Base de datos no inicializada');
                    return;
                }
                
                const transaction = db.transaction(['prices'], 'readwrite');
                const objectStore = transaction.objectStore('prices');
                
                // Limpiar el almacén de precios
                const clearRequest = objectStore.clear();
                
                clearRequest.onsuccess = function() {
                    // Agregar cada precio
                    Object.keys(membershipPrices).forEach(membership => {
                        const request = objectStore.add({
                            membership: membership,
                            price: membershipPrices[membership]
                        });
                        
                        request.onerror = function(event) {
                            console.error('Error al guardar precio para', membership, ':', event.target.error);
                        };
                    });
                    
                    console.log('Precios guardados en IndexedDB');
                };
                
                clearRequest.onerror = function(event) {
                    console.error('Error al limpiar precios:', event.target.error);
                };
            }
            
            // Calcular fecha de fin según el tipo de membresía
            function calculateEndDate(startDate, membership) {
                const date = new Date(startDate);
                
                switch(membership) {
                    case 'Mensual':
                        date.setMonth(date.getMonth() + 1);
                        break;
                    case 'Trimestral':
                        date.setMonth(date.getMonth() + 3);
                        break;
                    case 'Semestral':
                        date.setMonth(date.getMonth() + 6);
                        break;
                    case 'Anual':
                        date.setFullYear(date.getFullYear() + 1);
                        break;
                }
                
                return date.toISOString().split('T')[0];
            }
            
            // Determinar estado del cliente
            function determineStatus(endDate) {
                const today = new Date();
                today.setHours(0, 0, 0, 0); // Establecer a medianoche para comparar solo fechas
                
                const end = new Date(endDate);
                return end >= today ? 'active' : 'inactive';
            }
            
            // Formatear fecha
            function formatDate(dateString) {
                const date = new Date(dateString);
                return date.toLocaleDateString('es-ES');
            }
            
            // Renderizar tabla de clientes
            function renderClients(clientsToRender = clients) {
                clientsTableBody.innerHTML = '';
                
                if (clientsToRender.length === 0) {
                    clientsTableBody.style.display = 'none';
                    emptyState.style.display = 'block';
                    return;
                }
                
                clientsTableBody.style.display = 'table-row-group';
                emptyState.style.display = 'none';
                
                clientsToRender.forEach(client => {
                    const row = document.createElement('tr');
                    
                    const statusClass = client.status === 'active' ? 'status-active' : 'status-inactive';
                    const statusText = client.status === 'active' ? 'Activo' : 'Inactivo';
                    
                    row.innerHTML = `
                        <td>${client.id}</td>
                        <td>${client.name} ${client.lastName}</td>
                        <td>${client.phone}</td>
                        <td>${client.email || '-'}</td>
                        <td>${client.membership}</td>
                        <td>$${(client.price || 0).toFixed(2)}</td>
                        <td>${formatDate(client.startDate)}</td>
                        <td>${formatDate(client.endDate)}</td>
                        <td class="${statusClass}">${statusText}</td>
                        <td>
                            <div class="actions">
                                <button class="btn btn-sm btn-primary" onclick="editClient(${client.id})">
                                    <i class="fas fa-edit"></i> Editar
                                </button>
                                <button class="btn btn-sm btn-danger" onclick="deleteClient(${client.id})">
                                    <i class="fas fa-trash"></i> Eliminar
                                </button>
                            </div>
                        </td>
                    `;
                    
                    clientsTableBody.appendChild(row);
                });
            }
            
            // Actualizar estadísticas
            function updateStats() {
                const totalClients = clients.length;
                const activeClients = clients.filter(client => client.status === 'active').length;
                const inactiveClients = totalClients - activeClients;
                
                document.getElementById('totalClients').textContent = totalClients;
                document.getElementById('activeClients').textContent = activeClients;
                document.getElementById('inactiveClients').textContent = inactiveClients;
            }
            
            // Actualizar resumen de precios
            function updatePriceSummary() {
                document.getElementById('summaryMensual').textContent = `$${membershipPrices['Mensual'].toFixed(2)}`;
                document.getElementById('summaryTrimestral').textContent = `$${membershipPrices['Trimestral'].toFixed(2)}`;
                document.getElementById('summarySemestral').textContent = `$${membershipPrices['Semestral'].toFixed(2)}`;
                document.getElementById('summaryAnual').textContent = `$${membershipPrices['Anual'].toFixed(2)}`;
            }
            
            // Resetear formulario
            function resetForm() {
                clientForm.reset();
                membershipPriceDisplay.textContent = '';
                editingClientId = null;
                submitBtn.innerHTML = '<i class="fas fa-save"></i> Registrar Cliente';
                cancelEditBtn.style.display = 'none';
                formMode.textContent = '';
            }
            
            // Mostrar precio de membresía al seleccionar
            membershipSelect.addEventListener('change', function() {
                const membership = this.value;
                
                if (membership) {
                    const price = membershipPrices[membership];
                    membershipPriceDisplay.textContent = `Precio: $${price.toFixed(2)}`;
                } else {
                    membershipPriceDisplay.textContent = '';
                }
            });
            
            // Función para guardar cliente en IndexedDB
            function saveClientToIndexedDB(event) {
                event.preventDefault();
                
                console.log('Guardando cliente en IndexedDB');
                
                // Obtener valores del formulario
                const name = document.getElementById('name').value.trim();
                const lastName = document.getElementById('lastName').value.trim();
                const phone = document.getElementById('phone').value.trim();
                const email = document.getElementById('email').value.trim();
                const membership = document.getElementById('membership').value;
                const startDate = document.getElementById('startDate').value;
                
                console.log('Valores del formulario:', { name, lastName, phone, email, membership, startDate });
                
                // Validar campos obligatorios
                if (!name || !lastName || !phone || !membership || !startDate) {
                    console.log('Campos obligatorios faltantes');
                    showNotification('Por favor, completa todos los campos obligatorios', true);
                    return;
                }
                
                // Calcular fecha de fin y estado
                const endDate = calculateEndDate(startDate, membership);
                const status = determineStatus(endDate);
                const price = membershipPrices[membership] || 0;
                
                console.log('Fechas calculadas:', { startDate, endDate, status, price });
                
                // Crear objeto cliente
                const clientData = {
                    name,
                    lastName,
                    phone,
                    email,
                    membership,
                    startDate,
                    endDate,
                    status,
                    price
                };
                
                console.log('Datos del cliente:', clientData);
                
                // Guardar en IndexedDB
                if (!db) {
                    console.error('Base de datos no inicializada');
                    showNotification('Error: base de datos no disponible', true);
                    return;
                }
                
                const transaction = db.transaction(['clients'], 'readwrite');
                const objectStore = transaction.objectStore('clients');
                
                let request;
                
                if (editingClientId) {
                    // Actualizar cliente existente
                    clientData.id = editingClientId;
                    request = objectStore.put(clientData);
                    
                    request.onsuccess = function(event) {
                        console.log('Cliente actualizado en IndexedDB');
                        
                        // Actualizar el array local
                        const index = clients.findIndex(c => c.id === editingClientId);
                        if (index !== -1) {
                            clients[index] = clientData;
                        }
                        
                        // Actualizar interfaz
                        renderClients();
                        updateStats();
                        
                        // Limpiar formulario
                        resetForm();
                        
                        // Mostrar notificación
                        showNotification('Cliente actualizado exitosamente');
                    };
                } else {
                    // Agregar nuevo cliente
                    request = objectStore.add(clientData);
                    
                    request.onsuccess = function(event) {
                        const clientId = event.target.result;
                        console.log('Cliente guardado en IndexedDB con ID:', clientId);
                        
                        // Actualizar el array local
                        clientData.id = clientId;
                        clients.push(clientData);
                        
                        // Actualizar interfaz
                        renderClients();
                        updateStats();
                        
                        // Limpiar formulario
                        resetForm();
                        
                        // Mostrar notificación
                        showNotification('Cliente registrado exitosamente');
                    };
                }
                
                request.onerror = function(event) {
                    console.error('Error al guardar cliente en IndexedDB:', event.target.error);
                    showNotification('Error al registrar el cliente', true);
                };
            }
            
            // Guardar precios
            pricesForm.addEventListener('submit', function(e) {
                e.preventDefault();
                
                // Obtener valores del formulario
                membershipPrices['Mensual'] = parseFloat(document.getElementById('priceMensual').value);
                membershipPrices['Trimestral'] = parseFloat(document.getElementById('priceTrimestral').value);
                membershipPrices['Semestral'] = parseFloat(document.getElementById('priceSemestral').value);
                membershipPrices['Anual'] = parseFloat(document.getElementById('priceAnual').value);
                
                // Guardar en IndexedDB
                savePricesToDB();
                
                // Actualizar resumen de precios
                updatePriceSummary();
                
                // Actualizar el precio mostrado si hay una membresía seleccionada
                if (membershipSelect.value) {
                    membershipSelect.dispatchEvent(new Event('change'));
                }
                
                showNotification('Precios actualizados exitosamente');
            });
            
            // Editar cliente
            window.editClient = function(id) {
                const client = clients.find(c => c.id === id);
                if (client) {
                    // Cargar datos en el formulario
                    document.getElementById('name').value = client.name;
                    document.getElementById('lastName').value = client.lastName;
                    document.getElementById('phone').value = client.phone;
                    document.getElementById('email').value = client.email || '';
                    document.getElementById('membership').value = client.membership;
                    document.getElementById('startDate').value = client.startDate;
                    
                    // Mostrar el precio actual de la membresía
                    membershipSelect.dispatchEvent(new Event('change'));
                    
                    // Establecer modo de edición
                    editingClientId = id;
                    submitBtn.innerHTML = '<i class="fas fa-save"></i> Actualizar Cliente';
                    cancelEditBtn.style.display = 'inline-flex';
                    formMode.textContent = 'Modo de edición';
                    
                    // Cambiar a la pestaña de clientes
                    document.querySelector('[data-tab="clients"]').click();
                    
                    // Scroll al formulario
                    document.querySelector('.card').scrollIntoView({ behavior: 'smooth' });
                    
                    showNotification('Modifica los datos y haz clic en "Actualizar Cliente"', false, true);
                }
            };
            
            // Eliminar cliente
            window.deleteClient = function(id) {
                if (confirm('¿Estás seguro de que deseas eliminar este cliente? Esta acción no se puede deshacer.')) {
                    // Eliminar de IndexedDB
                    if (db) {
                        const transaction = db.transaction(['clients'], 'readwrite');
                        const objectStore = transaction.objectStore('clients');
                        const request = objectStore.delete(id);
                        
                        request.onsuccess = function() {
                            console.log('Cliente eliminado de IndexedDB');
                            
                            // Actualizar el array local
                            clients = clients.filter(client => client.id !== id);
                            
                            // Actualizar interfaz
                            renderClients();
                            updateStats();
                            showNotification('Cliente eliminado exitosamente');
                        };
                        
                        request.onerror = function(event) {
                            console.error('Error al eliminar cliente de IndexedDB:', event.target.error);
                            showNotification('Error al eliminar el cliente', true);
                        };
                    } else {
                        showNotification('Error: base de datos no disponible', true);
                    }
                }
            };
            
            // Cancelar edición
            cancelEditBtn.addEventListener('click', function() {
                resetForm();
                showNotification('Edición cancelada', false, true);
            });
            
            // Filtrar clientes
            function filterClients() {
                const searchTerm = searchInput.value.toLowerCase();
                const statusValue = statusFilter.value;
                
                let filteredClients = clients;
                
                if (searchTerm) {
                    filteredClients = filteredClients.filter(client => 
                        client.name.toLowerCase().includes(searchTerm) || 
                        client.lastName.toLowerCase().includes(searchTerm) || 
                        (client.email && client.email.toLowerCase().includes(searchTerm))
                    );
                }
                
                if (statusValue) {
                    filteredClients = filteredClients.filter(client => client.status === statusValue);
                }
                
                renderClients(filteredClients);
            }
            
            // Event listeners para filtros
            searchInput.addEventListener('input', filterClients);
            statusFilter.addEventListener('change', filterClients);
            
            // Limpiar filtros
            clearFiltersBtn.addEventListener('click', function() {
                searchInput.value = '';
                statusFilter.value = '';
                renderClients();
            });
            
            // Event listener para el formulario
            clientForm.addEventListener('submit', saveClientToIndexedDB);
            
            // Inicializar la aplicación
            console.log('Inicializando aplicación con IndexedDB');
            initIndexedDB();
        });
    </script>
</body>
</html>
