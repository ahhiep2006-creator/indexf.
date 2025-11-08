<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Trang Web Mẫu - Thực hành CSS Grid & Flexbox</title>
    <style>
        /* Reset và biến CSS */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        :root {
            --primary-color: #2c3e50;
            --secondary-color: #3498db;
            --accent-color: #e74c3c;
            --light-color: #ecf0f1;
            --dark-color: #2c3e50;
            --text-color: #333;
            --spacing-sm: 0.5rem;
            --spacing-md: 1rem;
            --spacing-lg: 2rem;
            --border-radius: 4px;
        }
        
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            color: var(--text-color);
            background-color: #f9f9f9;
        }
        
        /* Liên kết "Chuyển đến nội dung chính" */
        .skip-link {
            position: absolute;
            top: -40px;
            left: 6px;
            background-color: var(--primary-color);
            color: white;
            padding: var(--spacing-sm) var(--spacing-md);
            text-decoration: none;
            border-radius: 0 0 var(--border-radius) var(--border-radius);
            z-index: 1000;
            transition: top 0.3s;
        }
        
        .skip-link:focus {
            top: 0;
        }
        
        /* Header và Navigation */
        header {
            background-color: var(--primary-color);
            color: white;
            padding: var(--spacing-md) 0;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }
        
        .container {
            width: 90%;
            max-width: 1200px;
            margin: 0 auto;
        }
        
        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .logo {
            font-size: 1.5rem;
            font-weight: bold;
        }
        
        /* Navigation */
        nav ul {
            display: flex;
            list-style: none;
        }
        
        nav li {
            margin-left: var(--spacing-lg);
        }
        
        nav a {
            color: white;
            text-decoration: none;
            padding: var(--spacing-sm) var(--spacing-md);
            border-radius: var(--border-radius);
            transition: background-color 0.3s;
        }
        
        nav a:hover, 
        nav a:focus {
            background-color: rgba(255,255,255,0.1);
            outline: 2px solid white;
        }
        
        /* Main Content Layout */
        main {
            padding: var(--spacing-lg) 0;
        }
        
        .grid-container {
            display: grid;
            grid-template-columns: 1fr 3fr;
            gap: var(--spacing-lg);
        }
        
        /* Sidebar */
        aside {
            background-color: white;
            padding: var(--spacing-lg);
            border-radius: var(--border-radius);
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }
        
        .sidebar-widget {
            margin-bottom: var(--spacing-lg);
        }
        
        .sidebar-widget h3 {
            margin-bottom: var(--spacing-md);
            color: var(--primary-color);
            border-bottom: 2px solid var(--secondary-color);
            padding-bottom: var(--spacing-sm);
        }
        
        /* Main Content */
        .content {
            background-color: white;
            padding: var(--spacing-lg);
            border-radius: var(--border-radius);
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }
        
        .content-section {
            margin-bottom: var(--spacing-lg);
        }
        
        .content-section h2 {
            color: var(--primary-color);
            margin-bottom: var(--spacing-md);
            padding-bottom: var(--spacing-sm);
            border-bottom: 1px solid #eee;
        }
        
        /* Card Layout */
        .card-container {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: var(--spacing-md);
            margin-top: var(--spacing-md);
        }
        
        .card {
            background-color: var(--light-color);
            border-radius: var(--border-radius);
            overflow: hidden;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
            transition: transform 0.3s, box-shadow 0.3s;
        }
        
        .card:hover {
            transform: translateY(-5px);
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
        }
        
        .card-img {
            height: 150px;
            background-color: var(--secondary-color);
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-weight: bold;
        }
        
        .card-content {
            padding: var(--spacing-md);
        }
        
        .card h3 {
            margin-bottom: var(--spacing-sm);
            color: var(--primary-color);
        }
        
        /* Footer */
        footer {
            background-color: var(--dark-color);
            color: white;
            padding: var(--spacing-lg) 0;
            margin-top: var(--spacing-lg);
        }
        
        .footer-content {
            display: flex;
            justify-content: space-between;
            flex-wrap: wrap;
        }
        
        .footer-section {
            flex: 1;
            min-width: 250px;
            margin-bottom: var(--spacing-md);
        }
        
        .footer-section h3 {
            margin-bottom: var(--spacing-md);
            color: var(--light-color);
        }
        
        .footer-section ul {
            list-style: none;
        }
        
        .footer-section li {
            margin-bottom: var(--spacing-sm);
        }
        
        .footer-section a {
            color: #ddd;
            text-decoration: none;
        }
        
        .footer-section a:hover {
            color: white;
            text-decoration: underline;
        }
        
        .copyright {
            text-align: center;
            margin-top: var(--spacing-lg);
            padding-top: var(--spacing-md);
            border-top: 1px solid rgba(255,255,255,0.1);
        }
        
        /* Responsive Design */
        @media (max-width: 768px) {
            .grid-container {
                grid-template-columns: 1fr;
            }
            
            .header-content {
                flex-direction: column;
                text-align: center;
            }
            
            nav ul {
                margin-top: var(--spacing-md);
                justify-content: center;
            }
            
            nav li {
                margin: 0 var(--spacing-sm);
            }
            
            .footer-content {
                flex-direction: column;
            }
        }
        
        @media (max-width: 480px) {
            nav ul {
                flex-direction: column;
            }
            
            nav li {
                margin: var(--spacing-sm) 0;
            }
        }
    </style>
</head>
<body>
    <!-- Liên kết "Chuyển đến nội dung chính" -->
    <a href="#main-content" class="skip-link">Chuyển đến nội dung chính</a>
    
    <!-- Header và Navigation -->
    <header>
        <div class="container">
            <div class="header-content">
                <div class="logo">Website Mẫu</div>
                <nav aria-label="Menu chính">
                    <ul>
                        <li><a href="#home">Trang chủ</a></li>
                        <li><a href="#about">Giới thiệu</a></li>
                        <li><a href="#services">Dịch vụ</a></li>
                        <li><a href="#portfolio">Dự án</a></li>
                        <li><a href="#contact">Liên hệ</a></li>
                    </ul>
                </nav>
            </div>
        </div>
    </header>
    
    <!-- Main Content -->
    <main id="main-content" tabindex="-1">
        <div class="container">
            <div class="grid-container">
                <!-- Sidebar -->
                <aside>
                    <div class="sidebar-widget">
                        <h3>Tìm kiếm</h3>
                        <form role="search">
                            <input type="search" placeholder="Tìm kiếm..." aria-label="Tìm kiếm">
                            <button type="submit">Tìm</button>
                        </form>
                    </div>
                    
                    <div class="sidebar-widget">
                        <h3>Danh mục</h3>
                        <ul>
                            <li><a href="#">Thiết kế Web</a></li>
                            <li><a href="#">Phát triển Ứng dụng</a></li>
                            <li><a href="#">SEO & Marketing</a></li>
                            <li><a href="#">Tư vấn Công nghệ</a></li>
                        </ul>
                    </div>
                    
                    <div class="sidebar-widget">
                        <h3>Tin mới nhất</h3>
                        <ul>
                            <li><a href="#">Các xu hướng thiết kế web năm 2023</a></li>
                            <li><a href="#">Tại sao tốc độ tải trang quan trọng?</a></li>
                            <li><a href="#">Cách tối ưu hóa cho thiết bị di động</a></li>
                        </ul>
                    </div>
                </aside>
                
                <!-- Main Content Area -->
                <div class="content">
                    <section class="content-section" id="home">
                        <h1>Chào mừng đến với Website Mẫu</h1>
                        <p>Đây là trang web mẫu được thiết kế để thể hiện các kỹ năng CSS Grid và Flexbox, cùng với các tính năng truy cập web quan trọng.</p>
                    </section>
                    
                    <section class="content-section" id="about">
                        <h2>Giới thiệu về chúng tôi</h2>
                        <p>Chúng tôi là một nhóm các nhà phát triển web đam mê tạo ra các trang web đẹp mắt, chức năng và có thể truy cập được cho mọi người.</p>
                        <p>Chúng tôi tin rằng web nên là một nơi mà mọi người, bất kể khả năng hay thiết bị, đều có thể truy cập và sử dụng dễ dàng.</p>
                    </section>
                    
                    <section class="content-section" id="services">
                        <h2>Dịch vụ của chúng tôi</h2>
                        <div class="card-container">
                            <div class="card">
                                <div class="card-img">Thiết kế Web</div>
                                <div class="card-content">
                                    <h3>Thiết kế Web Responsive</h3>
                                    <p>Tạo các trang web đẹp mắt và hoạt động tốt trên mọi thiết bị.</p>
                                </div>
                            </div>
                            
                            <div class="card">
                                <div class="card-img">Phát triển Ứng dụng</div>
                                <div class="card-content">
                                    <h3>Phát triển Ứng dụng Web</h3>
                                    <p>Xây dựng các ứng dụng web hiện đại với công nghệ tiên tiến.</p>
                                </div>
                            </div>
                            
                            <div class="card">
                                <div class="card-img">Tối ưu hóa</div>
                                <div class="card-content">
                                    <h3>Tối ưu hóa SEO</h3>
                                    <p>Cải thiện thứ hạng tìm kiếm và tăng lưu lượng truy cập tự nhiên.</p>
                                </div>
                            </div>
                            
                            <div class="card">
                                <div class="card-img">Truy cập Web</div>
                                <div class="card-content">
                                    <h3>Kiểm tra Truy cập Web</h3>
                                    <p>Đảm bảo trang web của bạn có thể truy cập được cho mọi người.</p>
                                </div>
                            </div>
                        </div>
                    </section>
                    
                    <section class="content-section" id="portfolio">
                        <h2>Dự án tiêu biểu</h2>
                        <p>Dưới đây là một số dự án mà chúng tôi đã thực hiện:</p>
                        <div class="card-container">
                            <div class="card">
                                <div class="card-img">Dự án 1</div>
                                <div class="card-content">
                                    <h3>Website Thương mại Điện tử</h3>
                                    <p>Một trang web thương mại điện tử với giao diện người dùng trực quan.</p>
                                </div>
                            </div>
                            
                            <div class="card">
                                <div class="card-img">Dự án 2</div>
                                <div class="card-content">
                                    <h3>Ứng dụng Quản lý Doanh nghiệp</h3>
                                    <p>Ứng dụng web giúp quản lý hoạt động kinh doanh hiệu quả.</p>
                                </div>
                            </div>
                        </div>
                    </section>
                </div>
            </div>
        </div>
    </main>
    
    <!-- Footer -->
    <footer>
        <div class="container">
            <div class="footer-content">
                <div class="footer-section">
                    <h3>Về chúng tôi</h3>
                    <p>Chúng tôi tạo ra các trang web đẹp mắt, chức năng và có thể truy cập được cho mọi người.</p>
                </div>
                
                <div class="footer-section">
                    <h3>Liên kết nhanh</h3>
                    <ul>
                        <li><a href="#home">Trang chủ</a></li>
                        <li><a href="#about">Giới thiệu</a></li>
                        <li><a href="#services">Dịch vụ</a></li>
                        <li><a href="#portfolio">Dự án</a></li>
                        <li><a href="#contact">Liên hệ</a></li>
                    </ul>
                </div>
                
                <div class="footer-section">
                    <h3>Liên hệ</h3>
                    <ul>
                        <li>Email: info@example.com</li>
                        <li>Điện thoại: (012) 345-6789</li>
                        <li>Địa chỉ: 123 Đường ABC, Quận XYZ, TP.HCM</li>
                    </ul>
                </div>
            </div>
            
            <div class="copyright">
                <p>&copy; 2023 Website Mẫu. Tất cả các quyền được bảo lưu.</p>
            </div>
        </div>
    </footer>
</body>
</html>
