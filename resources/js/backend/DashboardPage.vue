<template>
  <AdminLayout>
    <div class="dashboard">
      <div class="dashboard-header">
        <h1 class="page-title">Dashboard</h1>
        <div class="dashboard-actions">
          <select v-model="timeFilter" class="form-select time-filter">
            <option value="month">Month</option>
            <option value="week">Week</option>
            <option value="day">Day</option>
          </select>
        </div>
      </div>
      
      <!-- Statistics Cards -->
      <div class="stats-grid">
        <div class="stat-card">
          <div class="stat-header">
            <span class="stat-label">PAGES</span>
            <i class="up-indicator fas fa-arrow-up"></i>
            <span class="change-indicator">03</span>
          </div>
          <div class="stat-value">{{ pagesCount }}</div>
          <div class="stat-chart">
            <div class="mini-chart"></div>
          </div>
        </div>
        
        <div class="stat-card">
          <div class="stat-header">
            <span class="stat-label">SECTIONS</span>
            <i class="up-indicator fas fa-arrow-up"></i>
            <span class="change-indicator">04</span>
          </div>
          <div class="stat-value">{{ sectionsCount }}</div>
          <div class="stat-chart">
            <div class="mini-chart"></div>
          </div>
        </div>
        
        <div class="stat-card">
          <div class="stat-header">
            <span class="stat-label">MESSAGES</span>
            <i class="up-indicator fas fa-arrow-up"></i>
            <span class="change-indicator">06</span>
          </div>
          <div class="stat-value">{{ messagesCount }}</div>
          <div class="stat-chart">
            <div class="mini-chart"></div>
          </div>
        </div>
        
        <div class="stat-card">
          <div class="stat-header">
            <span class="stat-label">MEDIA</span>
            <i class="up-indicator fas fa-arrow-up"></i>
            <span class="change-indicator">02</span>
          </div>
          <div class="stat-value">{{ mediaCount }}</div>
          <div class="stat-chart">
            <div class="mini-chart"></div>
          </div>
        </div>
      </div>
      
      <!-- Main Content Cards -->
      <div class="dashboard-main">
        <div class="content-row">
          <!-- Trend Chart -->
          <div class="content-card trend-chart">
            <div class="card-header">
              <h2>Activity Trend</h2>
            </div>
            <div class="card-content">
              <div class="chart-placeholder">
                <div class="subscription-trend"></div>
              </div>
            </div>
          </div>
          
          <!-- Recent Activity -->
          <div class="content-card recent-activity">
            <div class="card-header">
              <h2>Recent Activity</h2>
            </div>
            <div class="card-content">
              <div class="activity-item">
                <i class="fas fa-file-alt activity-icon"></i>
                <div class="activity-details">
                  <div class="activity-title">Number of Sessions</div>
                  <div class="activity-stats">
                    <span class="today-count">03 Today</span>
                    <span class="period-count">36 This month</span>
                  </div>
                </div>
              </div>
              
              <div class="activity-item">
                <i class="fas fa-graduation-cap activity-icon"></i>
                <div class="activity-details">
                  <div class="activity-title">Content Completion</div>
                  <div class="activity-stats">
                    <span class="today-count">01 Today</span>
                    <span class="period-count">12 This month</span>
                  </div>
                </div>
              </div>
              
              <div class="activity-item">
                <i class="fas fa-user activity-icon"></i>
                <div class="activity-details">
                  <div class="activity-title">User Enrollments</div>
                  <div class="activity-stats">
                    <span class="today-count">03 Today</span>
                    <span class="period-count">36 This month</span>
                  </div>
                </div>
              </div>
              
              <div class="activity-item">
                <i class="fas fa-users activity-icon"></i>
                <div class="activity-details">
                  <div class="activity-title">Groups Created</div>
                  <div class="activity-stats">
                    <span class="today-count">01 Today</span>
                    <span class="period-count">05 This month</span>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
        
        <div class="content-row">
          <!-- Circular Charts -->
          <div class="circular-charts">
            <div class="chart-card">
              <h3>Pages vs Sections</h3>
              <div class="circular-chart">
                <div class="chart-circle">
                  <span class="chart-number">{{ pagesCount }}</span>
                </div>
              </div>
              <div class="chart-legend">
                <div class="legend-item">
                  <span class="legend-color" style="background-color: #6c757d;"></span>
                  <span class="legend-text">Pages</span>
                </div>
                <div class="legend-item">
                  <span class="legend-color" style="background-color: #28a745;"></span>
                  <span class="legend-text">Sections</span>
                </div>
              </div>
            </div>
            
            <div class="chart-card">
              <h3>Content Types</h3>
              <div class="circular-chart">
                <div class="chart-circle">
                  <span class="chart-number">11</span>
                </div>
              </div>
              <div class="chart-legend">
                <div class="legend-item">
                  <span class="legend-color" style="background-color: #007bff;"></span>
                  <span class="legend-text">Text</span>
                  <span class="legend-value">03</span>
                </div>
                <div class="legend-item">
                  <span class="legend-color" style="background-color: #6610f2;"></span>
                  <span class="legend-text">Images</span>
                  <span class="legend-value">02</span>
                </div>
                <div class="legend-item">
                  <span class="legend-color" style="background-color: #6f42c1;"></span>
                  <span class="legend-text">Videos</span>
                  <span class="legend-value">01</span>
                </div>
              </div>
            </div>
            
            <div class="chart-card">
              <h3>Completion Status</h3>
              <div class="circular-chart">
                <div class="chart-circle">
                  <span class="chart-number">06</span>
                </div>
              </div>
              <div class="chart-legend">
                <div class="legend-item">
                  <span class="legend-color" style="background-color: #ffc107;"></span>
                  <span class="legend-text">Not started</span>
                  <span class="legend-value">03</span>
                </div>
                <div class="legend-item">
                  <span class="legend-color" style="background-color: #17a2b8;"></span>
                  <span class="legend-text">In Progress</span>
                  <span class="legend-value">02</span>
                </div>
                <div class="legend-item">
                  <span class="legend-color" style="background-color: #28a745;"></span>
                  <span class="legend-text">Completed</span>
                  <span class="legend-value">01</span>
                </div>
              </div>
            </div>
            
            <div class="chart-card">
              <h3>Groups</h3>
              <div class="circular-chart">
                <div class="chart-circle">
                  <span class="chart-number">10</span>
                </div>
              </div>
              <div class="chart-legend">
                <div class="legend-item">
                  <span class="legend-color" style="background-color: #20c997;"></span>
                  <span class="legend-text">Group 1</span>
                  <span class="legend-value">03</span>
                </div>
                <div class="legend-item">
                  <span class="legend-color" style="background-color: #e83e8c;"></span>
                  <span class="legend-text">Group 2</span>
                  <span class="legend-value">02</span>
                </div>
                <div class="legend-item">
                  <span class="legend-color" style="background-color: #fd7e14;"></span>
                  <span class="legend-text">Group 3</span>
                  <span class="legend-value">05</span>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
      
      <!-- Quick Actions -->
      <div class="quick-actions">
        <h2 class="section-title">Quick Actions</h2>
        <div class="actions-grid">
          <router-link to="/admin/pages" class="action-card">
            <div class="action-icon">
              <i class="fas fa-plus"></i>
            </div>
            <div class="action-text">Add New Page</div>
          </router-link>
          
          <router-link to="/admin/media" class="action-card">
            <div class="action-icon">
              <i class="fas fa-upload"></i>
            </div>
            <div class="action-text">Upload Media</div>
          </router-link>
          
          <router-link to="/admin/messages" class="action-card">
            <div class="action-icon">
              <i class="fas fa-envelope-open-text"></i>
            </div>
            <div class="action-text">Check Messages</div>
          </router-link>
          
          <a href="/" target="_blank" class="action-card">
            <div class="action-icon">
              <i class="fas fa-external-link-alt"></i>
            </div>
            <div class="action-text">View Website</div>
          </a>
        </div>
      </div>
    </div>
  </AdminLayout>
</template>

<script setup>
import { ref, onMounted, computed } from 'vue';
import axios from 'axios';
import AdminLayout from './AdminLayout.vue';
import { toast } from 'vue3-toastify';

// Data
const pages = ref([]);
const isLoading = ref(true);
const error = ref(null);
const recentMessages = ref([]);
const isLoadingMessages = ref(true);
const messageError = ref(null);
const unreadMessages = ref(0);
const mediaCount = ref(0);
const messagesCount = ref(0);
const timeFilter = ref('month');

// Computed properties
const pagesCount = computed(() => pages.value.length);
const sectionsCount = computed(() => {
  return pages.value.reduce((sum, page) => sum + (page.sections_count || 0), 0);
});

// Methods
const fetchPages = async () => {
  isLoading.value = true;
  error.value = null;
  
  try {
    const response = await axios.get('/api/admin/pages');
    pages.value = response.data.slice(0, 5); // Get the 5 most recent pages
  } catch (err) {
    console.error('Failed to load pages:', err);
    error.value = 'Failed to load pages. Please try again.';
    pages.value = [];
  } finally {
    isLoading.value = false;
  }
};

const fetchMessages = async () => {
  isLoadingMessages.value = true;
  messageError.value = null;
  
  try {
    const response = await axios.get('/api/admin/messages', {
      params: { per_page: 5 } // Get only 5 most recent messages
    });
    
    if (response.data.success) {
      if (response.data.data && response.data.data.data) {
        recentMessages.value = response.data.data.data;
        messagesCount.value = response.data.data.total;
      } else {
        recentMessages.value = response.data.data || [];
        messagesCount.value = recentMessages.value.length;
      }
      
      unreadMessages.value = response.data.unread_count || 0;
    } else {
      messageError.value = 'Failed to load messages';
      recentMessages.value = [];
    }
  } catch (err) {
    console.error('Failed to load messages:', err);
    messageError.value = 'Failed to load messages. Please try again.';
    recentMessages.value = [];
  } finally {
    isLoadingMessages.value = false;
  }
};

const fetchMediaCount = async () => {
  try {
    const response = await axios.get('/api/admin/media/count');
    mediaCount.value = response.data.count || 0;
  } catch (err) {
    console.error('Failed to load media count:', err);
    mediaCount.value = 0;
  }
};

const refreshDashboard = async () => {
  toast.info('Refreshing dashboard data...');
  await Promise.all([
    fetchPages(),
    fetchMessages(),
    fetchMediaCount()
  ]);
  toast.success('Dashboard refreshed!');
};

const truncateText = (text, length) => {
  if (!text) return '';
  return text.length > length ? text.substring(0, length) + '...' : text;
};

const formatDate = (dateString) => {
  const date = new Date(dateString);
  const now = new Date();
  const diff = Math.floor((now - date) / 1000 / 60); // Difference in minutes
  
  if (diff < 1) return 'Just now';
  if (diff < 60) return `${diff} min ago`;
  
  const hours = Math.floor(diff / 60);
  if (hours < 24) return `${hours} hour${hours > 1 ? 's' : ''} ago`;
  
  const days = Math.floor(hours / 24);
  if (days < 7) return `${days} day${days > 1 ? 's' : ''} ago`;
  
  return date.toLocaleDateString();
};

onMounted(() => {
  fetchPages();
  fetchMessages();
  fetchMediaCount();
});
</script>

<style scoped>
/* Light and dark mode variables */
:root {
  --light-bg: #f8f9fa;
  --light-card: #ffffff;
  --light-text: #212529;
  --light-text-secondary: #6c757d;
  --light-border: #f1f1f1;
  --light-chart-bg: rgba(61, 139, 253, 0.1);
  --light-shadow: 0 2px 6px rgba(0, 0, 0, 0.05);
  
  --dark-bg: #1e2124;
  --dark-card: #2d3238;
  --dark-text: #e9ecef;
  --dark-text-secondary: #adb5bd;
  --dark-border: #40454a;
  --dark-chart-bg: rgba(61, 139, 253, 0.15);
  --dark-shadow: 0 2px 6px rgba(0, 0, 0, 0.2);
  
  --primary-color: #3d8bfd;
  --primary-hover: #2d7af2;
  --danger-color: #dc3545;
}

.dashboard {
  padding: 1.5rem;
  background-color: var(--light-bg);
  color: var(--light-text);
}

[data-color-mode="dark"] .dashboard {
  background-color: var(--dark-bg);
  color: var(--dark-text);
}

.dashboard-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 1.5rem;
}

.page-title {
  margin: 0;
  color: var(--light-text);
  font-size: 1rem;
  font-weight: 600;
}

[data-color-mode="dark"] .page-title {
  color: var(--dark-text);
}

.time-filter {
  width: auto;
  min-width: 120px;
  background-color: var(--light-card);
  color: var(--light-text);
  border-color: var(--light-border);
}

[data-color-mode="dark"] .time-filter {
  background-color: var(--dark-card);
  color: var(--dark-text);
  border-color: var(--dark-border);
}

/* Statistics Cards */
.stats-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 1.5rem;
  margin-bottom: 2rem;
}

.stat-card {
  background-color: var(--light-card);
  border-radius: 8px;
  box-shadow: var(--light-shadow);
  padding: 1.25rem;
  display: flex;
  flex-direction: column;
  position: relative;
}

[data-color-mode="dark"] .stat-card {
  background-color: var(--dark-card);
  box-shadow: var(--dark-shadow);
}

.stat-header {
  display: flex;
  align-items: center;
  margin-bottom: 0.5rem;
}

.stat-label {
  color: var(--light-text-secondary);
  font-size: 0.875rem;
  font-weight: 600;
  text-transform: uppercase;
  flex-grow: 1;
}

[data-color-mode="dark"] .stat-label {
  color: var(--dark-text-secondary);
}

.change-indicator {
  color: #28a745;
  font-size: 0.75rem;
  font-weight: 600;
  margin-left: 0.25rem;
}

.up-indicator {
  color: #28a745;
  font-size: 0.75rem;
}

.stat-value {
  font-size: 2.25rem;
  font-weight: 600;
  color: var(--light-text);
  margin-bottom: 0.5rem;
}

[data-color-mode="dark"] .stat-value {
  color: var(--dark-text);
}

.stat-chart {
  height: 24px;
  margin-top: auto;
}

.mini-chart {
  height: 100%;
  background-image: linear-gradient(90deg, #e9ecef 0%, #e9ecef 20%, #dee2e6 20%, #dee2e6 40%, #ced4da 40%, #ced4da 60%, #adb5bd 60%, #adb5bd 80%, #6c757d 80%, #6c757d 100%);
  opacity: 0.5;
}

[data-color-mode="dark"] .mini-chart {
  background-image: linear-gradient(90deg, #495057 0%, #495057 20%, #5a6268 20%, #5a6268 40%, #6c757d 40%, #6c757d 60%, #7f8c8d 60%, #7f8c8d 80%, #95a5a6 80%, #95a5a6 100%);
}

/* Content Layout */
.dashboard-main {
  margin-bottom: 2rem;
}

.content-row {
  display: flex;
  gap: 1.5rem;
  margin-bottom: 1.5rem;
}

.content-card {
  background-color: var(--light-card);
  border-radius: 8px;
  box-shadow: var(--light-shadow);
  overflow: hidden;
  display: flex;
  flex-direction: column;
}

[data-color-mode="dark"] .content-card {
  background-color: var(--dark-card);
  box-shadow: var(--dark-shadow);
}

.trend-chart {
  flex: 3;
}

.recent-activity {
  flex: 2;
}

.card-header {
  padding: 1rem 1.5rem;
  border-bottom: 1px solid var(--light-border);
}

[data-color-mode="dark"] .card-header {
  border-bottom-color: var(--dark-border);
}

.card-header h2 {
  margin: 0;
  font-size: 1rem;
  color: var(--light-text);
  font-weight: 600;
}

[data-color-mode="dark"] .card-header h2 {
  color: var(--dark-text);
}

.card-content {
  flex: 1;
  padding: 1.5rem;
}

/* Activity Items */
.activity-item {
  display: flex;
  align-items: center;
  margin-bottom: 1.25rem;
  padding-bottom: 1.25rem;
  border-bottom: 1px solid var(--light-border);
}

[data-color-mode="dark"] .activity-item {
  border-bottom-color: var(--dark-border);
}

.activity-item:last-child {
  margin-bottom: 0;
  padding-bottom: 0;
  border-bottom: none;
}

.activity-icon {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  background-color: var(--light-bg);
  display: flex;
  align-items: center;
  justify-content: center;
  color: var(--light-text-secondary);
  margin-right: 1rem;
  font-size: 1.25rem;
}

[data-color-mode="dark"] .activity-icon {
  background-color: var(--dark-bg);
  color: var(--dark-text-secondary);
}

.activity-details {
  flex: 1;
}

.activity-title {
  font-weight: 500;
  margin-bottom: 0.25rem;
  color: var(--light-text);
}

[data-color-mode="dark"] .activity-title {
  color: var(--dark-text);
}

.activity-stats {
  display: flex;
  font-size: 0.875rem;
  color: var(--light-text-secondary);
}

[data-color-mode="dark"] .activity-stats {
  color: var(--dark-text-secondary);
}

.today-count {
  margin-right: 1rem;
  font-weight: 500;
  color: var(--light-text-secondary);
}

[data-color-mode="dark"] .today-count {
  color: var(--dark-text-secondary);
}

.period-count {
  color: var(--light-text-secondary);
  opacity: 0.7;
}

[data-color-mode="dark"] .period-count {
  color: var(--dark-text-secondary);
}

/* Trend Chart Placeholder */
.chart-placeholder {
  height: 200px;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
}

.subscription-trend {
  width: 100%;
  height: 100%;
  background-image: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="100%" height="100%" viewBox="0 0 100 50"><polyline points="0,40 10,35 20,30 30,38 40,32 50,20 60,25 70,30 80,25 90,28 100,22" fill="none" stroke="%236c757d" stroke-width="2"/></svg>');
  background-repeat: no-repeat;
  background-position: center;
  background-size: 100% 100%;
}

[data-color-mode="dark"] .subscription-trend {
  background-image: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="100%" height="100%" viewBox="0 0 100 50"><polyline points="0,40 10,35 20,30 30,38 40,32 50,20 60,25 70,30 80,25 90,28 100,22" fill="none" stroke="%23adb5bd" stroke-width="2"/></svg>');
}

/* Circular Charts */
.circular-charts {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 1.5rem;
  width: 100%;
}

.chart-card {
  background-color: var(--light-card);
  border-radius: 8px;
  box-shadow: var(--light-shadow);
  padding: 1.25rem;
  text-align: center;
}

[data-color-mode="dark"] .chart-card {
  background-color: var(--dark-card);
  box-shadow: var(--dark-shadow);
}

.chart-card h3 {
  margin: 0 0 1rem;
  font-size: 0.9rem;
  color: var(--light-text-secondary);
  font-weight: 600;
}

[data-color-mode="dark"] .chart-card h3 {
  color: var(--dark-text-secondary);
}

.circular-chart {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-bottom: 1rem;
}

.chart-circle {
  width: 100px;
  height: 100px;
  border-radius: 50%;
  border: 10px solid var(--light-border);
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
}

[data-color-mode="dark"] .chart-circle {
  border-color: var(--dark-border);
}

.chart-circle::before {
  content: '';
  position: absolute;
  top: -10px;
  left: -10px;
  width: 100px;
  height: 100px;
  border-radius: 50%;
  border: 10px solid var(--primary-color);
  border-color: var(--primary-color) transparent transparent transparent;
  transform: rotate(45deg);
}

.chart-number {
  font-size: 1.75rem;
  font-weight: 600;
  color: var(--light-text);
}

[data-color-mode="dark"] .chart-number {
  color: var(--dark-text);
}

.chart-legend {
  text-align: left;
}

.legend-item {
  display: flex;
  align-items: center;
  margin-bottom: 0.5rem;
  font-size: 0.8rem;
}

.legend-color {
  width: 12px;
  height: 12px;
  border-radius: 2px;
  margin-right: 0.5rem;
}

.legend-text {
  color: var(--light-text-secondary);
  flex-grow: 1;
}

[data-color-mode="dark"] .legend-text {
  color: var(--dark-text-secondary);
}

.legend-value {
  color: var(--light-text);
  font-weight: 500;
}

[data-color-mode="dark"] .legend-value {
  color: var(--dark-text);
}

/* Quick Actions */
.quick-actions {
  margin-bottom: 2rem;
}

.section-title {
  margin-bottom: 1rem;
  font-size: 1rem;
  color: var(--light-text);
  font-weight: 600;
}

[data-color-mode="dark"] .section-title {
  color: var(--dark-text);
}

.actions-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
  gap: 1rem;
}

.action-card {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 1.25rem;
  background-color: var(--light-card);
  border-radius: 8px;
  box-shadow: var(--light-shadow);
  transition: transform 0.2s, box-shadow 0.2s;
  text-decoration: none;
  color: var(--light-text);
}

[data-color-mode="dark"] .action-card {
  background-color: var(--dark-card);
  color: var(--dark-text);
  box-shadow: var(--dark-shadow);
}

.action-card:hover {
  transform: translateY(-3px);
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
}

[data-color-mode="dark"] .action-card:hover {
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.3);
}

.action-icon {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  background-color: var(--light-bg);
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 0.75rem;
  font-size: 1rem;
  color: var(--light-text-secondary);
}

[data-color-mode="dark"] .action-icon {
  background-color: var(--dark-bg);
  color: var(--primary-color);
}

.action-text {
  font-weight: 500;
  text-align: center;
  font-size: 0.875rem;
  color: var(--light-text);
}

[data-color-mode="dark"] .action-text {
  color: var(--dark-text);
}

/* Responsive Adjustments */
@media (max-width: 1200px) {
  .stats-grid {
    grid-template-columns: repeat(2, 1fr);
  }
  
  .circular-charts {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 992px) {
  .content-row {
    flex-direction: column;
  }
  
  .trend-chart,
  .recent-activity {
    width: 100%;
  }
}

@media (max-width: 768px) {
  .circular-charts {
    grid-template-columns: 1fr;
  }
}

@media (max-width: 576px) {
  .stats-grid {
    grid-template-columns: 1fr;
  }
}

/* RTL Support */
[dir="rtl"] .activity-icon {
  margin-right: 0;
  margin-left: 1rem;
}

[dir="rtl"] .today-count {
  margin-right: 0;
  margin-left: 1rem;
}

[dir="rtl"] .legend-color {
  margin-right: 0;
  margin-left: 0.5rem;
}

[dir="rtl"] .chart-legend {
  text-align: right;
}
</style> 