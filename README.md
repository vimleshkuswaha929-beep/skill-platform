<!DOCTYPE html>
<html lang="hi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SkillPixo - Earn Money with Skills</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: #333;
            line-height: 1.6;
            min-height: 100vh;
        }

        /* Background Pattern */
        .background-pattern {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: 
                radial-gradient(circle at 20% 80%, rgba(120, 119, 198, 0.3) 0%, transparent 50%),
                radial-gradient(circle at 80% 20%, rgba(255, 119, 198, 0.3) 0%, transparent 50%),
                radial-gradient(circle at 40% 40%, rgba(120, 219, 255, 0.2) 0%, transparent 50%);
            animation: float 6s ease-in-out infinite;
            z-index: -1;
        }

        @keyframes float {
            0%, 100% { transform: translateY(0px) rotate(0deg); }
            50% { transform: translateY(-20px) rotate(1deg); }
        }

        /* Header Styles */
        header {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            color: #333;
            padding: 1rem 0;
            box-shadow: 0 2px 20px rgba(0,0,0,0.1);
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 1000;
        }

        .navbar {
            display: flex;
            justify-content: space-between;
            align-items: center;
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* Custom Logo Styles */
        .logo-container {
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .logo-icon {
            width: 45px;
            height: 45px;
            background: linear-gradient(135deg, #667eea, #764ba2);
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            box-shadow: 0 4px 15px rgba(102, 126, 234, 0.4);
        }

        .logo-icon::before {
            content: "₹";
            font-size: 24px;
            font-weight: bold;
            color: white;
            text-shadow: 1px 1px 2px rgba(0,0,0,0.3);
        }

        .logo-text {
            display: flex;
            flex-direction: column;
            line-height: 1;
        }

        .logo-main {
            font-size: 1.8rem;
            font-weight: 800;
            background: linear-gradient(135deg, #667eea, #764ba2);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            letter-spacing: -0.5px;
        }

        .logo-main .letter-s {
            font-size: 2.2rem;
            background: linear-gradient(135deg, #ff6b6b, #ffa36b);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            display: inline-block;
            transform: translateY(2px);
            text-shadow: 2px 2px 4px rgba(255, 107, 107, 0.3);
        }

        .logo-tagline {
            font-size: 0.7rem;
            color: #666;
            font-weight: 500;
            letter-spacing: 0.5px;
            margin-top: 2px;
        }

        /* Navigation Links */
        .nav-links {
            display: flex;
            list-style: none;
            gap: 2rem;
            align-items: center;
        }

        .nav-links a {
            color: #333;
            text-decoration: none;
            transition: color 0.3s;
            font-weight: 500;
            padding: 8px 12px;
            border-radius: 8px;
        }

        .nav-links a:hover {
            color: #667eea;
            background: rgba(102, 126, 234, 0.1);
        }

        /* Login/Signup Button */
        .login-btn {
            background: linear-gradient(135deg, #667eea, #764ba2);
            color: white;
            padding: 10px 20px;
            border: none;
            border-radius: 25px;
            cursor: pointer;
            transition: transform 0.3s;
            font-weight: 600;
        }

        .login-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(102, 126, 234, 0.4);
        }

        /* User Dashboard */
        .user-dashboard {
            display: none;
            align-items: center;
            gap: 1rem;
        }

        .user-avatar {
            width: 40px;
            height: 40px;
            background: linear-gradient(135deg, #667eea, #764ba2);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-weight: bold;
            font-size: 1.1rem;
        }

        .user-name {
            font-weight: 600;
            color: #333;
        }

        .logout-btn {
            background: #ff6b6b;
            color: white;
            padding: 8px 15px;
            border: none;
            border-radius: 20px;
            cursor: pointer;
            font-size: 0.9rem;
            transition: transform 0.3s;
        }

        .logout-btn:hover {
            transform: translateY(-2px);
        }

        .admin-btn {
            background: #9c27b0;
            color: white;
            padding: 8px 15px;
            border: none;
            border-radius: 20px;
            cursor: pointer;
            font-size: 0.9rem;
            transition: transform 0.3s;
        }

        .admin-btn:hover {
            transform: translateY(-2px);
        }

        /* Auto Withdrawal Badge */
        .auto-withdrawal-badge {
            background: linear-gradient(135deg, #06D6A0, #118AB2);
            color: white;
            padding: 5px 10px;
            border-radius: 15px;
            font-size: 0.8rem;
            font-weight: bold;
            display: inline-flex;
            align-items: center;
            gap: 5px;
        }

        /* Hamburger Menu */
        .menu-toggle {
            display: none;
            flex-direction: column;
            cursor: pointer;
            padding: 5px;
        }

        .menu-toggle span {
            width: 25px;
            height: 3px;
            background: #667eea;
            margin: 3px 0;
            transition: 0.3s;
            border-radius: 2px;
        }

        /* Top Three Line Stats */
        .top-stats {
            max-width: 1200px;
            margin: 100px auto 20px;
            padding: 0 20px;
        }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 1.5rem;
            margin-bottom: 2rem;
        }

        .stat-box {
            background: rgba(255, 255, 255, 0.95);
            border-radius: 20px;
            padding: 2rem;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
            backdrop-filter: blur(10px);
            text-align: center;
            border: 3px solid;
            transition: transform 0.3s;
        }

        .stat-box:hover {
            transform: translateY(-5px);
        }

        .stat-box.affiliate {
            border-color: #667eea;
        }

        .stat-box.earnings {
            border-color: #06D6A0;
        }

        .stat-box.support {
            border-color: #ff6b6b;
        }

        .stat-icon {
            font-size: 3rem;
            margin-bottom: 1rem;
        }

        .stat-box.affiliate .stat-icon { color: #667eea; }
        .stat-box.earnings .stat-icon { color: #06D6A0; }
        .stat-box.support .stat-icon { color: #ff6b6b; }

        .stat-box h3 {
            font-size: 1.5rem;
            margin-bottom: 1rem;
            color: #333;
        }

        .stat-box p {
            color: #666;
            margin-bottom: 1rem;
        }

        /* Hero Section */
        .hero {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            color: white;
            text-align: center;
            padding: 150px 20px 100px;
            margin-top: 80px;
            border-radius: 0 0 50px 50px;
        }

        .hero-logo {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 15px;
            margin-bottom: 2rem;
        }

        .hero-logo-icon {
            width: 80px;
            height: 80px;
            background: linear-gradient(135deg, #667eea, #764ba2);
            border-radius: 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: 0 8px 25px rgba(102, 126, 234, 0.5);
        }

        .hero-logo-icon::before {
            content: "₹";
            font-size: 40px;
            font-weight: bold;
            color: white;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
        }

        .hero-logo-text {
            text-align: left;
        }

        .hero-logo-main {
            font-size: 3.5rem;
            font-weight: 800;
            background: linear-gradient(135deg, #fff, #e0e7ff);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            letter-spacing: -1px;
            line-height: 1;
        }

        .hero-logo-main .letter-s {
            font-size: 4.2rem;
            background: linear-gradient(135deg, #ff6b6b, #ffd166);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            display: inline-block;
            transform: translateY(5px);
            text-shadow: 3px 3px 6px rgba(255, 107, 107, 0.4);
        }

        .hero-logo-tagline {
            font-size: 1.1rem;
            color: rgba(255, 255, 255, 0.9);
            font-weight: 500;
            letter-spacing: 1px;
            margin-top: 5px;
            text-shadow: 1px 1px 2px rgba(0,0,0,0.3);
        }

        .hero p {
            font-size: 1.3rem;
            margin-bottom: 2rem;
            opacity: 0.9;
        }

        .cta-button {
            background: linear-gradient(135deg, #ff6b6b, #ffa36b);
            color: white;
            padding: 15px 35px;
            border: none;
            border-radius: 30px;
            font-size: 1.1rem;
            cursor: pointer;
            transition: transform 0.3s, box-shadow 0.3s;
            box-shadow: 0 5px 15px rgba(255, 107, 107, 0.4);
            font-weight: 600;
        }

        .cta-button:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 25px rgba(255, 107, 107, 0.6);
        }

        /* Auto Scroll Thumbnails */
        .thumbnail-slider {
            max-width: 1200px;
            margin: 2rem auto;
            padding: 0 20px;
            position: relative;
        }

        .slider-container {
            overflow: hidden;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.3);
        }

        .slider-track {
            display: flex;
            transition: transform 0.5s ease-in-out;
            animation: autoScroll 15s infinite linear;
        }

        .thumbnail-slide {
            min-width: 100%;
            height: 400px;
            position: relative;
        }

        .thumbnail-slide img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .slide-content {
            position: absolute;
            bottom: 0;
            left: 0;
            right: 0;
            background: linear-gradient(transparent, rgba(0,0,0,0.8));
            color: white;
            padding: 2rem;
            text-align: center;
        }

        .slide-content h3 {
            font-size: 2rem;
            margin-bottom: 0.5rem;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.5);
        }

        .slide-content p {
            font-size: 1.1rem;
            opacity: 0.9;
        }

        @keyframes autoScroll {
            0% { transform: translateX(0%); }
            33% { transform: translateX(0%); }
            36% { transform: translateX(-100%); }
            66% { transform: translateX(-100%); }
            69% { transform: translateX(-200%); }
            97% { transform: translateX(-200%); }
            100% { transform: translateX(0%); }
        }

        /* Sections Common Styles */
        .section-title {
            text-align: center;
            margin-bottom: 3rem;
            font-size: 2.5rem;
            color: white;
            text-shadow: 2px 2px 10px rgba(0,0,0,0.3);
        }

        .courses, .earnings, .founders-bottom, .dashboard {
            max-width: 1200px;
            margin: 50px auto;
            padding: 0 20px;
        }

        /* Earnings Section */
        .earnings-card {
            background: rgba(255, 255, 255, 0.95);
            border-radius: 20px;
            padding: 2rem;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
            backdrop-filter: blur(10px);
            text-align: center;
            margin-bottom: 2rem;
        }

        .earnings-stats {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 1rem;
            margin-top: 2rem;
        }

        .stat-card {
            color: white;
            padding: 1.5rem;
            border-radius: 15px;
            text-align: center;
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
        }

        .stat-card.total-earnings {
            background: linear-gradient(135deg, #667eea, #764ba2);
        }

        .stat-card.total-sales {
            background: linear-gradient(135deg, #ff6b6b, #ffa36b);
        }

        .stat-card.this-month {
            background: linear-gradient(135deg, #4CAF50, #45a049);
        }

        .stat-card.pending-payout {
            background: linear-gradient(135deg, #9c27b0, #673ab7);
        }

        .stat-number {
            font-size: 2rem;
            font-weight: bold;
            margin-bottom: 0.5rem;
        }

        .stat-label {
            font-size: 0.9rem;
            opacity: 0.9;
        }

        /* Auto Withdrawal Section */
        .auto-withdrawal-card {
            background: rgba(255, 255, 255, 0.95);
            border-radius: 20px;
            padding: 2rem;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
            margin-bottom: 2rem;
            border: 3px solid #06D6A0;
        }

        .auto-withdrawal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 1.5rem;
        }

        .auto-status {
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .toggle-switch {
            position: relative;
            display: inline-block;
            width: 60px;
            height: 30px;
        }

        .toggle-switch input {
            opacity: 0;
            width: 0;
            height: 0;
        }

        .toggle-slider {
            position: absolute;
            cursor: pointer;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background-color: #ccc;
            transition: .4s;
            border-radius: 34px;
        }

        .toggle-slider:before {
            position: absolute;
            content: "";
            height: 22px;
            width: 22px;
            left: 4px;
            bottom: 4px;
            background-color: white;
            transition: .4s;
            border-radius: 50%;
        }

        input:checked + .toggle-slider {
            background-color: #06D6A0;
        }

        input:checked + .toggle-slider:before {
            transform: translateX(30px);
        }

        .auto-schedule {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 1rem;
            margin: 1.5rem 0;
        }

        .schedule-item {
            background: #f8f9fa;
            padding: 1rem;
            border-radius: 10px;
            text-align: center;
        }

        .schedule-item.active {
            background: #e3f2fd;
            border: 2px solid #2196f3;
        }

        /* Courses Section */
        .course-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
        }

        .course-card {
            background: rgba(255, 255, 255, 0.95);
            border-radius: 20px;
            padding: 2rem;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
            transition: transform 0.3s, box-shadow 0.3s;
            backdrop-filter: blur(10px);
            position: relative;
        }

        .course-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 20px 40px rgba(0,0,0,0.3);
        }

        .course-image {
            width: 100%;
            height: 180px;
            border-radius: 15px;
            object-fit: cover;
            margin-bottom: 1rem;
            border: 3px solid #f0f0f0;
        }

        .course-card h3 {
            color: #333;
            margin-bottom: 1rem;
            text-align: center;
            font-size: 1.3rem;
            min-height: 60px;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .course-card p {
            color: #666;
            margin-bottom: 1.5rem;
            text-align: center;
            min-height: 40px;
        }

        .price {
            color: #667eea;
            font-size: 1.8rem;
            font-weight: bold;
            margin: 1rem 0;
            text-align: center;
        }

        .commission-badge {
            position: absolute;
            top: -10px;
            right: -10px;
            background: linear-gradient(135deg, #ff6b6b, #ffa36b);
            color: white;
            padding: 8px 15px;
            border-radius: 20px;
            font-weight: bold;
            font-size: 0.8rem;
            box-shadow: 0 5px 15px rgba(255, 107, 107, 0.4);
        }

        /* Course Actions */
        .course-actions {
            display: flex;
            flex-direction: column;
            gap: 10px;
            margin-top: 1rem;
        }

        .buy-now-btn {
            background: linear-gradient(135deg, #06D6A0, #118AB2);
            color: white;
            padding: 12px 25px;
            border: none;
            border-radius: 25px;
            cursor: pointer;
            transition: transform 0.3s;
            font-weight: bold;
        }

        .buy-now-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(6, 214, 160, 0.4);
        }

        .affiliate-btn {
            background: linear-gradient(135deg, #667eea, #764ba2);
            color: white;
            padding: 12px 25px;
            border: none;
            border-radius: 25px;
            cursor: pointer;
            width: 100%;
            transition: transform 0.3s;
            font-weight: bold;
        }

        .affiliate-btn:hover {
            transform: translateY(-2px);
        }

        /* Course Specific Colors */
        .course-1 { border-top: 5px solid #FF6B6B; }
        .course-2 { border-top: 5px solid #4ECDC4; }
        .course-3 { border-top: 5px solid #FFD166; }
        .course-4 { border-top: 5px solid #06D6A0; }
        .course-5 { border-top: 5px solid #118AB2; }

        /* Withdrawal System */
        .withdrawal-card {
            background: rgba(255, 255, 255, 0.95);
            border-radius: 20px;
            padding: 2rem;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
            margin-bottom: 2rem;
        }

        .withdrawal-form {
            display: grid;
            gap: 1rem;
            margin-top: 1.5rem;
        }

        .withdrawal-options {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
            gap: 1rem;
            margin: 1rem 0;
        }

        .withdrawal-option {
            padding: 1rem;
            border: 2px solid #e0e0e0;
            border-radius: 10px;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s;
        }

        .withdrawal-option.selected {
            border-color: #667eea;
            background: rgba(102, 126, 234, 0.1);
        }

        .withdrawal-option i {
            font-size: 2rem;
            margin-bottom: 0.5rem;
            color: #667eea;
        }

        .withdrawal-history {
            margin-top: 2rem;
        }

        .withdrawal-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 1rem;
            border-bottom: 1px solid #f0f0f0;
        }

        .withdrawal-status {
            padding: 5px 10px;
            border-radius: 15px;
            font-size: 0.8rem;
            font-weight: bold;
        }

        .status-pending { background: #fff3e0; color: #ff9800; }
        .status-approved { background: #e8f5e8; color: #4caf50; }
        .status-rejected { background: #ffebee; color: #f44336; }
        .status-paid { background: #e3f2fd; color: #2196f3; }
        .status-auto { background: #e8f5e8; color: #06D6A0; }

        /* Founders Section */
        .founders-title {
            text-align: center;
            margin-bottom: 3rem;
            font-size: 2.5rem;
            color: white;
            text-shadow: 2px 2px 10px rgba(0,0,0,0.3);
        }

        .founders-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(500px, 1fr));
            gap: 3rem;
            margin-top: 1rem;
        }

        .founder-card {
            background: rgba(255, 255, 255, 0.95);
            border-radius: 20px;
            padding: 2rem;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
            backdrop-filter: blur(10px);
            text-align: center;
            transition: transform 0.3s, box-shadow 0.3s;
        }

        .founder-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 40px rgba(0,0,0,0.3);
        }

        .founder-image-container {
            position: relative;
            margin: 0 auto 1.5rem;
            width: 250px;
            height: 350px;
            border-radius: 20px;
            overflow: hidden;
            box-shadow: 0 10px 30px rgba(0,0,0,0.3);
        }

        .founder-image {
            width: 100%;
            height: 100%;
            object-fit: cover;
            border: 6px solid;
        }

        .ceo-image {
            border-color: #667eea;
        }

        .cofounder-image {
            border-color: #ff6b6b;
        }

        .founder-info {
            text-align: center;
        }

        .founder-name {
            font-size: 2rem;
            font-weight: bold;
            margin-bottom: 0.5rem;
        }

        .ceo-name {
            background: linear-gradient(135deg, #667eea, #764ba2);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .cofounder-name {
            background: linear-gradient(135deg, #ff6b6b, #ffa36b);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .founder-title {
            font-size: 1.3rem;
            font-weight: 600;
            margin-bottom: 1rem;
            padding: 8px 20px;
            border-radius: 25px;
            display: inline-block;
            color: white;
        }

        .ceo-title {
            background: linear-gradient(135deg, #667eea, #764ba2);
        }

        .cofounder-title {
            background: linear-gradient(135deg, #ff6b6b, #ffa36b);
        }

        .founder-description {
            color: #666;
            font-size: 1rem;
            line-height: 1.6;
            margin-bottom: 1rem;
            text-align: center;
        }

        .founder-quote {
            font-style: italic;
            color: #667eea;
            padding: 1rem;
            border-radius: 10px;
            background: rgba(102, 126, 234, 0.1);
            margin-top: 1rem;
            font-size: 1.1rem;
        }

        .ceo-quote {
            border-left: 4px solid #667eea;
            color: #667eea;
        }

        .cofounder-quote {
            border-left: 4px solid #ff6b6b;
            color: #ff6b6b;
        }

        /* Admin Panel */
        .admin-panel {
            display: none;
        }

        .admin-stats {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 1rem;
            margin: 2rem 0;
        }

        .admin-stat-card {
            background: white;
            padding: 1.5rem;
            border-radius: 15px;
            text-align: center;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
        }

        .admin-table {
            background: white;
            border-radius: 15px;
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
            margin: 2rem 0;
        }

        .admin-table table {
            width: 100%;
            border-collapse: collapse;
        }

        .admin-table th,
        .admin-table td {
            padding: 1rem;
            text-align: left;
            border-bottom: 1px solid #f0f0f0;
        }

        .admin-table th {
            background: #f8f9fa;
            font-weight: 600;
        }

        .action-btn {
            padding: 5px 10px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            margin: 0 2px;
            font-size: 0.8rem;
        }

        .approve-btn { background: #4caf50; color: white; }
        .reject-btn { background: #f44336; color: white; }
        .pay-btn { background: #2196f3; color: white; }

        /* Modal Styles */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.5);
            z-index: 2000;
            backdrop-filter: blur(5px);
        }

        .modal-content {
            background: white;
            padding: 2rem;
            border-radius: 20px;
            width: 90%;
            max-width: 500px;
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            box-shadow: 0 20px 40px rgba(0,0,0,0.3);
            max-height: 90vh;
            overflow-y: auto;
        }

        .close {
            float: right;
            font-size: 1.5rem;
            cursor: pointer;
            color: #666;
        }

        .form-group {
            margin-bottom: 1rem;
        }

        .form-group label {
            display: block;
            margin-bottom: 0.5rem;
            color: #333;
            font-weight: 500;
        }

        .form-group input, .form-group select {
            width: 100%;
            padding: 12px;
            border: 2px solid #e0e0e0;
            border-radius: 10px;
            font-size: 1rem;
            transition: border-color 0.3s;
        }

        .form-group input:focus, .form-group select:focus {
            outline: none;
            border-color: #667eea;
        }

        .submit-btn {
            background: linear-gradient(135deg, #667eea, #764ba2);
            color: white;
            padding: 12px;
            border: none;
            border-radius: 10px;
            width: 100%;
            font-size: 1rem;
            cursor: pointer;
            transition: transform 0.3s;
            font-weight: 600;
        }

        .submit-btn:hover {
            transform: translateY(-2px);
        }

        .withdraw-btn {
            background: linear-gradient(135deg, #06D6A0, #118AB2);
            color: white;
            padding: 12px 25px;
            border: none;
            border-radius: 25px;
            cursor: pointer;
            font-weight: bold;
            margin-top: 1rem;
        }

        /* Countdown Timer */
        .countdown-timer {
            background: linear-gradient(135deg, #667eea, #764ba2);
            color: white;
            padding: 1rem;
            border-radius: 10px;
            text-align: center;
            margin: 1rem 0;
        }

        .countdown-numbers {
            display: flex;
            justify-content: center;
            gap: 1rem;
            margin: 1rem 0;
        }

        .countdown-item {
            text-align: center;
        }

        .countdown-value {
            font-size: 2rem;
            font-weight: bold;
            display: block;
        }

        .countdown-label {
            font-size: 0.8rem;
            opacity: 0.8;
        }

        /* Footer */
        footer {
            background: rgba(0, 0, 0, 0.8);
            color: white;
            text-align: center;
            padding: 2rem 0;
            margin-top: 50px;
            backdrop-filter: blur(10px);
        }

        .contact-info {
            margin: 1rem 0;
        }

        .contact-info a {
            color: #fdbb2d;
            text-decoration: none;
            margin: 0 10px;
        }

        .contact-info a:hover {
            text-decoration: underline;
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            .menu-toggle {
                display: flex;
            }

            .nav-links {
                position: fixed;
                top: 80px;
                left: -100%;
                width: 100%;
                height: calc(100vh - 80px);
                background: rgba(255, 255, 255, 0.98);
                backdrop-filter: blur(10px);
                flex-direction: column;
                justify-content: flex-start;
                align-items: center;
                padding-top: 2rem;
                transition: left 0.3s ease;
                gap: 1.5rem;
            }

            .nav-links.active {
                left: 0;
            }

            .nav-links a {
                font-size: 1.1rem;
                padding: 15px 20px;
                width: 80%;
                text-align: center;
                border-radius: 10px;
                background: rgba(102, 126, 234, 0.05);
            }

            .logo-main {
                font-size: 1.5rem;
            }

            .logo-main .letter-s {
                font-size: 1.8rem;
            }

            .logo-tagline {
                font-size: 0.6rem;
            }

            .founders-container {
                grid-template-columns: 1fr;
                gap: 1.5rem;
            }

            .founder-image-container {
                width: 200px;
                height: 280px;
            }

            .founder-name {
                font-size: 1.6rem;
            }

            .hero-logo {
                flex-direction: column;
                gap: 10px;
            }

            .hero-logo-text {
                text-align: center;
            }

            .hero-logo-main {
                font-size: 2.8rem;
            }

            .hero-logo-main .letter-s {
                font-size: 3.2rem;
            }

            .hero h1 {
                font-size: 2.5rem;
            }

            .hero p {
                font-size: 1.1rem;
            }

            .course-grid {
                grid-template-columns: 1fr;
            }
            
            .course-card h3 {
                font-size: 1.2rem;
                min-height: auto;
            }

            .earnings-stats {
                grid-template-columns: 1fr;
            }

            .course-modal-header {
                flex-direction: column;
                text-align: center;
            }

            .course-modal-image {
                width: 100%;
                height: 150px;
            }

            .withdrawal-options {
                grid-template-columns: 1fr;
            }

            .auto-schedule {
                grid-template-columns: 1fr;
            }

            .admin-table {
                overflow-x: auto;
            }

            .countdown-numbers {
                gap: 0.5rem;
            }

            .countdown-value {
                font-size: 1.5rem;
            }

            .thumbnail-slide {
                height: 300px;
            }

            .slide-content h3 {
                font-size: 1.5rem;
            }

            .slide-content p {
                font-size: 1rem;
            }

            .stats-grid {
                grid-template-columns: 1fr;
            }

            .top-stats {
                margin-top: 120px;
            }
        }
    </style>
</head>
<body>
    <!-- Background Pattern -->
    <div class="background-pattern"></div>

    <!-- Header -->
    <header>
        <nav class="navbar">
            <div class="logo-container">
                <div class="logo-icon"></div>
                <div class="logo-text">
                    <div class="logo-main">
                        <span class="letter-s">S</span>kill<span style="color: #667eea">Pixo</span>
                    </div>
                    <div class="logo-tagline">Earn While You Learn</div>
                </div>
            </div>

            <!-- Hamburger Menu -->
            <div class="menu-toggle" id="menuToggle">
                <span></span>
                <span></span>
                <span></span>
            </div>

            <ul class="nav-links" id="navLinks">
                <li><a href="#home">Home</a></li>
                <li><a href="#earnings">My Earnings</a></li>
                <li><a href="#courses">Courses</a></li>
                <li><a href="#auto-withdrawal">Auto Withdrawal</a></li>
                <li><a href="#withdrawal">Withdraw Money</a></li>
                <li><a href="#about">About Us</a></li>
            </ul>

            <!-- User Dashboard -->
            <div class="user-dashboard" id="userDashboard">
                <div class="user-avatar" id="userAvatar">U</div>
                <div class="user-name" id="userName">User</div>
                <button class="admin-btn" id="adminBtn" style="display: none;">Admin Panel</button>
                <button class="logout-btn" id="logoutBtn">Logout</button>
            </div>

            <!-- Login Button -->
            <button class="login-btn" id="loginBtn">Login/Signup</button>
        </nav>
    </header>

    <!-- Top Three Line Stats -->
    <section class="top-stats">
        <div class="stats-grid">
            <div class="stat-box affiliate">
                <div class="stat-icon">
                    <i class="fas fa-users"></i>
                </div>
                <h3>Become an Affiliate</h3>
                <p>Join our affiliate program and start earning 75% commission on every course sale. Share your unique link and watch your income grow!</p>
                <button class="cta-button" onclick="showModal('loginModal')">Join Now</button>
            </div>

            <div class="stat-box earnings">
                <div class="stat-icon">
                    <i class="fas fa-chart-line"></i>
                </div>
                <h3>High Commissions</h3>
                <p>Earn 75% commission on every sale! We believe in sharing success with our affiliates. The more you sell, the more you earn.</p>
                <button class="cta-button" onclick="showCoursesSection()">View Courses</button>
            </div>

            <div class="stat-box support">
                <div class="stat-icon">
                    <i class="fas fa-headset"></i>
                </div>
                <h3>24/7 Support</h3>
                <p>Get dedicated support for all your queries. Our team is always available to help you succeed in your affiliate journey.</p>
                <button class="cta-button" onclick="document.getElementById('contact').scrollIntoView({behavior: 'smooth'})">Contact Us</button>
            </div>
        </div>
    </section>

    <!-- Hero Section -->
    <section class="hero" id="home">
        <div class="hero-logo">
            <div class="hero-logo-icon"></div>
            <div class="hero-logo-text">
                <div class="hero-logo-main">
                    <span class="letter-s">S</span>kill<span style="color: transparent">Pixo</span>
                </div>
                <div class="hero-logo-tagline">EARN WHILE YOU LEARN</div>
            </div>
        </div>
        <p>सीखो, Promote करो, और पैसा कमाओ! Join India's Fastest Growing Affiliate Platform</p>
        <button class="cta-button" onclick="showCoursesSection()">Start Earning Today</button>
    </section>

    <!-- Auto Scroll Thumbnails Section -->
    <section class="thumbnail-slider">
        <div class="slider-container">
            <div class="slider-track">
                <!-- Thumbnail 1 -->
                <div class="thumbnail-slide">
                    <img src="https://i.ibb.co/6R0ZNRJZ/Screenshot-2025-11-19-225231.png" alt="Digital Marketing Course">
                    <div class="slide-content">
                        <h3>Digital Marketing Mastery</h3>
                        <p>Learn to earn with trending digital marketing skills</p>
                    </div>
                </div>
                
                <!-- Thumbnail 2 -->
                <div class="thumbnail-slide">
                    <img src="https://i.ibb.co/BVnCCvkd/Summer-Trip-To-London-Vlog.png" alt="Video Editing Course">
                    <div class="slide-content">
                        <h3>Video Editing Expert</h3>
                        <p>Master video editing and create viral content</p>
                    </div>
                </div>
                
                <!-- Thumbnail 3 -->
                <div class="thumbnail-slide">
                    <img src="https://i.ibb.co/XfrbDRfz/Black-First-Fortnight-Stream.png" alt="Content Creation">
                    <div class="slide-content">
                        <h3>Stock Market Trading</h3>
                        <p>Learn trading strategies and earn from stock market</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- My Earnings Section -->
    <section class="earnings" id="earnings">
        <h2 class="section-title">My Affiliate Dashboard</h2>
        <div class="earnings-card">
            <h3>Your Earnings Overview</h3>
            
            <div class="earnings-stats">
                <div class="stat-card total-earnings">
                    <div class="stat-number">₹<span id="totalEarnings">0</span></div>
                    <div class="stat-label">Total Earnings</div>
                </div>
                <div class="stat-card total-sales">
                    <div class="stat-number" id="totalSales">0</div>
                    <div class="stat-label">Total Sales</div>
                </div>
                <div class="stat-card this-month">
                    <div class="stat-number">₹<span id="thisMonthEarnings">0</span></div>
                    <div class="stat-label">This Month</div>
                </div>
                <div class="stat-card pending-payout">
                    <div class="stat-number">₹<span id="availableBalance">0</span></div>
                    <div class="stat-label">Available Balance</div>
                </div>
            </div>
        </div>
    </section>

    <!-- Courses Section -->
    <section class="courses" id="courses">
        <h2 class="section-title">Popular Courses</h2>
        <div class="course-grid">
            <!-- Course 1 - Personal Branding -->
            <div class="course-card course-1">
                <div class="commission-badge">75% Commission</div>
                <img src="https://images.unsplash.com/photo-1611224923853-80b023f02d71?w=400&h=250&fit=crop" alt="Personal Branding" class="course-image">
                <h3>Personal Branding</h3>
                <p>Build your powerful personal brand online and stand out from the crowd</p>
                <div class="price">₹499</div>
                <div class="course-actions">
                    <button class="buy-now-btn" onclick="showCourseDetails('personal-branding')">
                        <i class="fas fa-shopping-cart"></i> Buy Now
                    </button>
                    <button class="affiliate-btn" onclick="getAffiliateLink('personal-branding')">
                        <i class="fas fa-share-alt"></i> Get Affiliate Link
                    </button>
                </div>
            </div>

            <!-- Course 2 - Digital Marketing -->
            <div class="course-card course-2">
                <div class="commission-badge">75% Commission</div>
                <img src="https://images.unsplash.com/photo-1551288049-bebda4e38f71?w=400&h=250&fit=crop" alt="Digital Marketing" class="course-image">
                <h3>Digital Marketing Mastery</h3>
                <p>Complete digital marketing strategies & techniques for 2024</p>
                <div class="price">₹999</div>
                <div class="course-actions">
                    <button class="buy-now-btn" onclick="showCourseDetails('digital-marketing')">
                        <i class="fas fa-shopping-cart"></i> Buy Now
                    </button>
                    <button class="affiliate-btn" onclick="getAffiliateLink('digital-marketing')">
                        <i class="fas fa-share-alt"></i> Get Affiliate Link
                    </button>
                </div>
            </div>

            <!-- Course 3 - Reels Editing -->
            <div class="course-card course-3">
                <div class="commission-badge">75% Commission</div>
                <img src="https://images.unsplash.com/photo-1611162617474-5b21e879e113?w=400&h=250&fit=crop" alt="Reels Editing" class="course-image">
                <h3>Trending Reels Editing</h3>
                <p>Master viral reels creation and editing techniques for social media</p>
                <div class="price">₹1,499</div>
                <div class="course-actions">
                    <button class="buy-now-btn" onclick="showCourseDetails('reels-editing')">
                        <i class="fas fa-shopping-cart"></i> Buy Now
                    </button>
                    <button class="affiliate-btn" onclick="getAffiliateLink('reels-editing')">
                        <i class="fas fa-share-alt"></i> Get Affiliate Link
                    </button>
                </div>
            </div>

            <!-- Course 4 - Stock Market Trading -->
            <div class="course-card course-4">
                <div class="commission-badge">75% Commission</div>
                <img src="https://images.unsplash.com/photo-1590283603385-17ffb3a7f29f?w=400&h=250&fit=crop" alt="Stock Market Trading" class="course-image">
                <h3>Stock Market Trading</h3>
                <p>Learn stock market trading strategies and investment techniques</p>
                <div class="price">₹1,999</div>
                <div class="course-actions">
                    <button class="buy-now-btn" onclick="showCourseDetails('stock-market-trading')">
                        <i class="fas fa-shopping-cart"></i> Buy Now
                    </button>
                    <button class="affiliate-btn" onclick="getAffiliateLink('stock-market-trading')">
                        <i class="fas fa-share-alt"></i> Get Affiliate Link
                    </button>
                </div>
            </div>

            <!-- Course 5 - Video Editing Expert -->
            <div class="course-card course-5">
                <div class="commission-badge">75% Commission</div>
                <img src="https://images.unsplash.com/photo-1551288049-bebda4e38f71?w=400&h=250&fit=crop" alt="Video Editing Expert" class="course-image">
                <h3>Video Editing Expert</h3>
                <p>Become a professional video editor with advanced techniques</p>
                <div class="price">₹2,499</div>
                <div class="course-actions">
                    <button class="buy-now-btn" onclick="showCourseDetails('video-editing-expert')">
                        <i class="fas fa-shopping-cart"></i> Buy Now
                    </button>
                    <button class="affiliate-btn" onclick="getAffiliateLink('video-editing-expert')">
                        <i class="fas fa-share-alt"></i> Get Affiliate Link
                    </button>
                </div>
            </div>
        </div>
    </section>

    <!-- Auto Withdrawal Section -->
    <section class="earnings" id="auto-withdrawal">
        <h2 class="section-title">Auto Withdrawal System</h2>
        
        <div class="auto-withdrawal-card">
            <div class="auto-withdrawal-header">
                <h3>Automatic Weekly Payout</h3>
                <div class="auto-status">
                    <span class="auto-withdrawal-badge">
                        <i class="fas fa-robot"></i>
                        AUTO PAYOUT
                    </span>
                    <label class="toggle-switch">
                        <input type="checkbox" id="autoWithdrawalToggle" checked>
                        <span class="toggle-slider"></span>
                    </label>
                </div>
            </div>

            <p>Enable auto withdrawal to automatically receive your earnings every week without manual requests!</p>

            <!-- Countdown Timer -->
            <div class="countdown-timer">
                <h4>Next Auto Payout In:</h4>
                <div class="countdown-numbers">
                    <div class="countdown-item">
                        <span class="countdown-value" id="countdownDays">0</span>
                        <span class="countdown-label">Days</span>
                    </div>
                    <div class="countdown-item">
                        <span class="countdown-value" id="countdownHours">0</span>
                        <span class="countdown-label">Hours</span>
                    </div>
                    <div class="countdown-item">
                        <span class="countdown-value" id="countdownMinutes">0</span>
                        <span class="countdown-label">Minutes</span>
                    </div>
                    <div class="countdown-item">
                        <span class="countdown-value" id="countdownSeconds">0</span>
                        <span class="countdown-label">Seconds</span>
                    </div>
                </div>
                <p><small>Every Monday at 10:00 AM</small></p>
            </div>

            <div class="auto-schedule">
                <div class="schedule-item active">
                    <h4>Next Payout</h4>
                    <p id="nextPayoutDate">Loading...</p>
                    <p>₹<span id="nextPayoutAmount">0</span></p>
                </div>
                <div class="schedule-item">
                    <h4>Last Payout</h4>
                    <p id="lastPayoutDate">-</p>
                    <p>₹<span id="lastPayoutAmount">0</span></p>
                </div>
                <div class="schedule-item">
                    <h4>Total Auto Paid</h4>
                    <p>All Time</p>
                    <p>₹<span id="totalAutoPaid">0</span></p>
                </div>
            </div>

            <div class="withdrawal-options">
                <div class="withdrawal-option selected" onclick="selectAutoWithdrawalMethod('upi')">
                    <i class="fas fa-mobile-alt"></i>
                    <h4>UPI</h4>
                    <p>Primary Method</p>
                </div>
                <div class="withdrawal-option" onclick="selectAutoWithdrawalMethod('bank')">
                    <i class="fas fa-university"></i>
                    <h4>Bank Transfer</h4>
                    <p>Backup Method</p>
                </div>
            </div>

            <div class="form-group">
                <label for="autoUpiId">UPI ID for Auto Payout</label>
                <input type="text" id="autoUpiId" placeholder="yourname@upi" value="user@ybl">
            </div>

            <button class="withdraw-btn" onclick="saveAutoWithdrawalSettings()">
                <i class="fas fa-save"></i> Save Auto Settings
            </button>
        </div>
    </section>

    <!-- Manual Withdrawal Section -->
    <section class="earnings" id="withdrawal">
        <h2 class="section-title">Manual Withdrawal</h2>
        
        <div class="withdrawal-card">
            <h3>Available Balance: ₹<span id="withdrawBalance">0</span></h3>
            <p>Minimum withdrawal amount: ₹100</p>
            
            <div class="withdrawal-options">
                <div class="withdrawal-option" onclick="selectWithdrawalMethod('upi')">
                    <i class="fas fa-mobile-alt"></i>
                    <h4>UPI</h4>
                    <p>Instant Transfer</p>
                </div>
                <div class="withdrawal-option" onclick="selectWithdrawalMethod('bank')">
                    <i class="fas fa-university"></i>
                    <h4>Bank Transfer</h4>
                    <p>1-2 Business Days</p>
                </div>
                <div class="withdrawal-option" onclick="selectWithdrawalMethod('paytm')">
                    <i class="fab fa-paytm"></i>
                    <h4>Paytm</h4>
                    <p>Instant Transfer</p>
                </div>
            </div>

            <form class="withdrawal-form" id="withdrawalForm">
                <div class="form-group">
                    <label for="withdrawAmount">Amount to Withdraw (₹)</label>
                    <input type="number" id="withdrawAmount" placeholder="Enter amount" min="100" required>
                </div>

                <div class="form-group" id="upiDetails" style="display: none;">
                    <label for="upiId">UPI ID</label>
                    <input type="text" id="upiId" placeholder="yourname@upi">
                </div>

                <div class="form-group" id="bankDetails" style="display: none;">
                    <label for="accountNumber">Account Number</label>
                    <input type="text" id="accountNumber" placeholder="Enter account number">
                    <label for="ifscCode">IFSC Code</label>
                    <input type="text" id="ifscCode" placeholder="Enter IFSC code">
                </div>

                <div class="form-group" id="paytmDetails" style="display: none;">
                    <label for="paytmNumber">Paytm Number</label>
                    <input type="text" id="paytmNumber" placeholder="Enter Paytm number">
                </div>

                <button type="submit" class="submit-btn">Request Withdrawal</button>
            </form>
        </div>

        <div class="withdrawal-card">
            <h3>Withdrawal History</h3>
            <div class="withdrawal-history" id="withdrawalHistory">
                <!-- Withdrawal history will be loaded here -->
            </div>
        </div>
    </section>

    <!-- About Us Section -->
    <section class="courses" id="about">
        <h2 class="section-title">About SkillPixo</h2>
        <div class="earnings-card">
            <h3>Our Mission</h3>
            <p>SkillPixo is dedicated to helping individuals earn money by promoting valuable skills courses. We believe everyone should have the opportunity to monetize their network and knowledge. With our 75% commission structure, we ensure our affiliates get the maximum share of earnings.</p>
            <div style="margin-top: 2rem;">
                <button class="affiliate-btn" style="max-width: 250px;" onclick="showModal('loginModal')">Join Our Team</button>
            </div>
        </div>
    </section>

    <!-- Founders Section at Bottom -->
    <section class="founders-bottom">
        <h2 class="founders-title">Meet Our Founders</h2>
        <div class="founders-container">
            <!-- CEO -->
            <div class="founder-card">
                <div class="founder-image-container">
                    <img src="https://i.ibb.co/prng3hk8/AKASH.jpg" alt="Mr. Akash Kushwaha - CEO & Founder" class="founder-image ceo-image">
                </div>
                <div class="founder-info">
                    <h3 class="founder-name ceo-name">MR. AKASH KUSHWAHA</h3>
                    <div class="founder-title ceo-title">CEO & FOUNDER</div>
                    <p class="founder-description">
                        With a vision to empower individuals through skill development and financial independence, 
                        Mr. Akash Kushwaha founded SkillPixo to bridge the gap between learning and earning. 
                        His entrepreneurial journey and passion for education have inspired thousands to 
                        monetize their skills through affiliate marketing.
                    </p>
                    <p class="founder-quote ceo-quote">
                        "Our mission is to create opportunities where skills meet earnings, and dreams meet reality. We believe in sharing success - that's why affiliates get 75% commission!"
                    </p>
                </div>
            </div>

            <!-- Co-Founder -->
            <div class="founder-card">
                <div class="founder-image-container">
                    <img src="https://i.ibb.co/vvMZGFxJ/1761933390087.jpg" alt="Mr. Vimlesh Kushwaha - Co-Founder" class="founder-image cofounder-image">
                </div>
                <div class="founder-info">
                    <h3 class="founder-name cofounder-name">MR. VIMLESH KUSHWAHA</h3>
                    <div class="founder-title cofounder-title">CO-FOUNDER</div>
                    <p class="founder-description">
                        Mr. Vimlesh Kushwaha brings extensive experience in business strategy and operations 
                        to SkillPixo. His expertise in scaling businesses and building sustainable models 
                        has been instrumental in shaping the platform's growth and success in the ed-tech space.
                    </p>
                    <p class="founder-quote cofounder-quote">
                        "Together, we're building a platform that transforms lives through education and entrepreneurship. Our 75-25 commission model ensures everyone wins!"
                    </p>
                </div>
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section class="courses" id="contact">
        <h2 class="section-title">Contact Us</h2>
        <div class="earnings-card">
            <h3>Get In Touch</h3>
            <p>Have questions? We're here to help you succeed!</p>
            <div class="contact-info">
                <p><strong>Phone:</strong> 
                    <a href="tel:+918840559303">+91 8840559303</a> | 
                    <a href="tel:+918707540294">+91 8707540294</a>
                </p>
                <p><strong>Email:</strong> info@skillpixo.com</p>
                <p><strong>Address:</strong> Delhi, India</p>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <p>&copy; 2025 SkillPixo. All rights reserved.</p>
        <div class="contact-info">
            <strong>Contact Us:</strong><br>
            <a href="tel:+918840559303">+91 8840559303</a> | 
            <a href="tel:+918707540294">+91 8707540294</a>
        </div>
        <p>Email: info@skillpixo.com</p>
        <p style="margin-top: 1rem;">Your Skills + Our Platform = Unlimited Earnings! 🚀</p>
    </footer>

    <!-- Admin Panel -->
    <section class="admin-panel" id="adminPanel">
        <h2 class="section-title">Admin Dashboard</h2>
        
        <div class="earnings-card">
            <h3>Platform Overview</h3>
            <div class="admin-stats">
                <div class="admin-stat-card">
                    <div class="stat-number">₹<span id="totalPlatformEarnings">0</span></div>
                    <div class="stat-label">Total Platform Earnings</div>
                </div>
                <div class="admin-stat-card">
                    <div class="stat-number" id="totalUsers">0</div>
                    <div class="stat-label">Total Users</div>
                </div>
                <div class="admin-stat-card">
                    <div class="stat-number" id="totalWithdrawals">0</div>
                    <div class="stat-label">Total Withdrawals</div>
                </div>
                <div class="admin-stat-card">
                    <div class="stat-number">₹<span id="adminBalance">0</span></div>
                    <div class="stat-label">Admin Balance (25%)</div>
                </div>
            </div>
        </div>

        <div class="earnings-card">
            <h3>Auto Withdrawal Settings</h3>
            <div class="form-group">
                <label>Auto Payout Day</label>
                <select id="adminPayoutDay" onchange="updateAutoPayoutDay()">
                    <option value="1">Monday</option>
                    <option value="2">Tuesday</option>
                    <option value="3">Wednesday</option>
                    <option value="4">Thursday</option>
                    <option value="5">Friday</option>
                </select>
            </div>
            <button class="withdraw-btn" onclick="runAutoPayoutNow()">
                <i class="fas fa-bolt"></i> Run Auto Payout Now
            </button>
        </div>

        <div class="earnings-card">
            <h3>Withdrawal Requests</h3>
            <div class="admin-table">
                <table>
                    <thead>
                        <tr>
                            <th>User</th>
                            <th>Amount</th>
                            <th>Method</th>
                            <th>Date</th>
                            <th>Status</th>
                            <th>Type</th>
                            <th>Actions</th>
                        </tr>
                    </thead>
                    <tbody id="adminWithdrawalTable">
                        <!-- Withdrawal requests will be loaded here -->
                    </tbody>
                </table>
            </div>
        </div>

        <div class="earnings-card">
            <h3>Admin Withdrawal</h3>
            <p>Your Admin Balance: ₹<span id="adminWithdrawBalance">0</span></p>
            <button class="withdraw-btn" onclick="showAdminWithdrawal()">
                <i class="fas fa-rupee-sign"></i> Withdraw Admin Earnings
            </button>
        </div>
    </section>

    <!-- Login/Signup Modal -->
    <div class="modal" id="loginModal">
        <div class="modal-content">
            <span class="close" id="closeModal">&times;</span>
            <h2 style="text-align: center; margin-bottom: 1.5rem;">Join SkillPixo</h2>
            
            <div style="text-align: center; margin-bottom: 1.5rem;">
                <button class="cta-button" onclick="showSignupForm()" style="margin: 5px;">Sign Up</button>
                <button class="cta-button" onclick="showLoginForm()" style="margin: 5px; background: linear-gradient(135deg, #667eea, #764ba2);">Login</button>
            </div>

            <!-- Signup Form -->
            <form id="signupForm" style="display: none;">
                <div class="form-group">
                    <label for="fullName">Full Name</label>
                    <input type="text" id="fullName" placeholder="Enter your full name" required>
                </div>
                <div class="form-group">
                    <label for="signupPhone">Phone Number</label>
                    <input type="tel" id="signupPhone" placeholder="Enter your 10-digit phone number" required maxlength="10">
                </div>
                <div class="form-group">
                    <label for="email">Email Address</label>
                    <input type="email" id="email" placeholder="Enter your email address" required>
                </div>
                <div class="form-group">
                    <label for="referralCode">Referral Code (Optional)</label>
                    <input type="text" id="referralCode" placeholder="Enter referral code if any">
                </div>
                <button type="submit" class="submit-btn">Create Account</button>
            </form>

            <!-- Login Form -->
            <form id="phoneLoginForm">
                <div class="form-group">
                    <label for="phoneNumber">Phone Number</label>
                    <input type="tel" id="phoneNumber" placeholder="Enter your 10-digit phone number" required maxlength="10">
                </div>
                
                <button type="submit" class="submit-btn">Send OTP</button>
            </form>

            <div class="otp-container" id="otpContainer" style="display: none;">
                <h3 style="text-align: center; margin: 1rem 0;">Enter OTP</h3>
                <div class="otp-inputs" style="display: flex; justify-content: center; gap: 10px; margin: 1rem 0;">
                    <input type="text" class="otp-input" maxlength="1" style="width: 40px; height: 40px; text-align: center; border: 2px solid #e0e0e0; border-radius: 5px;">
                    <input type="text" class="otp-input" maxlength="1" style="width: 40px; height: 40px; text-align: center; border: 2px solid #e0e0e0; border-radius: 5px;">
                    <input type="text" class="otp-input" maxlength="1" style="width: 40px; height: 40px; text-align: center; border: 2px solid #e0e0e0; border-radius: 5px;">
                    <input type="text" class="otp-input" maxlength="1" style="width: 40px; height: 40px; text-align: center; border: 2px solid #e0e0e0; border-radius: 5px;">
                </div>
                
                <button type="button" class="submit-btn" id="verifyOtpBtn">Verify OTP</button>
            </div>
        </div>
    </div>

    <!-- Admin Withdrawal Modal -->
    <div class="modal" id="adminWithdrawalModal">
        <div class="modal-content">
            <span class="close" onclick="closeModal('adminWithdrawalModal')">&times;</span>
            <h2 style="text-align: center; margin-bottom: 1.5rem;">Withdraw Admin Earnings</h2>
            
            <div class="form-group">
                <label>Available Balance: ₹<span id="adminAvailableBalance">0</span></label>
            </div>

            <div class="form-group">
                <label for="adminWithdrawAmount">Amount to Withdraw (₹)</label>
                <input type="number" id="adminWithdrawAmount" placeholder="Enter amount" min="100" required>
            </div>

            <div class="form-group">
                <label for="adminBankDetails">Bank Account Details</label>
                <select id="adminBankDetails" class="form-group">
                    <option value="">Select Bank Account</option>
                    <option value="icici">ICICI Bank - XXXX XXXX 1234</option>
                    <option value="hdfc">HDFC Bank - XXXX XXXX 5678</option>
                </select>
            </div>

            <button class="submit-btn" onclick="processAdminWithdrawal()">Process Withdrawal</button>
        </div>
    </div>

    <script>
        // Global Variables
        let currentUser = null;
        let otp = '';
        let selectedCourse = null;
        let selectedWithdrawalMethod = '';
        let selectedAutoWithdrawalMethod = 'upi';
        const ADMIN_PHONE = '8840559303'; // Your CEO phone number
        let autoWithdrawalInterval;

        // Course Data with 75% commission and exact prices
        const courses = {
            'personal-branding': { title: 'Personal Branding', price: 499, commission: 0.75 },
            'digital-marketing': { title: 'Digital Marketing Mastery', price: 999, commission: 0.75 },
            'reels-editing': { title: 'Trending Reels Editing', price: 1499, commission: 0.75 },
            'stock-market-trading': { title: 'Stock Market Trading', price: 1999, commission: 0.75 },
            'video-editing-expert': { title: 'Video Editing Expert', price: 2499, commission: 0.75 }
        };

        // Initialize the application
        document.addEventListener('DOMContentLoaded', function() {
            initializeApp();
            startCountdownTimer();
            initializeAutoWithdrawal();
            setupMobileMenu();
        });

        function setupMobileMenu() {
            const menuToggle = document.getElementById('menuToggle');
            const navLinks = document.getElementById('navLinks');

            menuToggle.addEventListener('click', function() {
                navLinks.classList.toggle('active');
                // Animate hamburger to X
                const spans = menuToggle.getElementsByTagName('span');
                if (navLinks.classList.contains('active')) {
                    spans[0].style.transform = 'rotate(45deg) translate(5px, 5px)';
                    spans[1].style.opacity = '0';
                    spans[2].style.transform = 'rotate(-45deg) translate(7px, -6px)';
                } else {
                    spans[0].style.transform = 'none';
                    spans[1].style.opacity = '1';
                    spans[2].style.transform = 'none';
                }
            });

            // Close menu when clicking on links
            const navLinksArray = document.querySelectorAll('.nav-links a');
            navLinksArray.forEach(link => {
                link.addEventListener('click', function() {
                    navLinks.classList.remove('active');
                    const spans = menuToggle.getElementsByTagName('span');
                    spans[0].style.transform = 'none';
                    spans[1].style.opacity = '1';
                    spans[2].style.transform = 'none';
                });
            });
        }

        function initializeApp() {
            // Check if user is already logged in
            const savedUser = localStorage.getItem('currentUser');
            if (savedUser) {
                currentUser = JSON.parse(savedUser);
                updateUserInterface();
                loadUserData();
            }

            // Setup event listeners
            setupEventListeners();
        }

        function setupEventListeners() {
            // Login Form
            document.getElementById('phoneLoginForm').addEventListener('submit', handleLogin);
            document.getElementById('verifyOtpBtn').addEventListener('click', verifyOtp);
            
            // Signup Form
            document.getElementById('signupForm').addEventListener('submit', handleSignup);
            
            // Withdrawal Form
            document.getElementById('withdrawalForm').addEventListener('submit', handleWithdrawal);
            
            // Auto Withdrawal Toggle
            document.getElementById('autoWithdrawalToggle').addEventListener('change', toggleAutoWithdrawal);
            
            // Navigation
            document.getElementById('loginBtn').addEventListener('click', () => showModal('loginModal'));
            document.getElementById('logoutBtn').addEventListener('click', handleLogout);
            document.getElementById('adminBtn').addEventListener('click', showAdminPanel);
            
            // Modal close buttons
            document.getElementById('closeModal').addEventListener('click', () => closeModal('loginModal'));
            
            // OTP input auto focus
            setupOtpInputs();
        }

        function showSignupForm() {
            document.getElementById('signupForm').style.display = 'block';
            document.getElementById('phoneLoginForm').style.display = 'none';
            document.getElementById('otpContainer').style.display = 'none';
        }

        function showLoginForm() {
            document.getElementById('signupForm').style.display = 'none';
            document.getElementById('phoneLoginForm').style.display = 'block';
            document.getElementById('otpContainer').style.display = 'none';
        }

        function handleSignup(e) {
            e.preventDefault();
            const fullName = document.getElementById('fullName').value;
            const phone = document.getElementById('signupPhone').value;
            const email = document.getElementById('email').value;
            const referralCode = document.getElementById('referralCode').value;

            if (phone.length === 10 && /^[6-9]\d{9}$/.test(phone)) {
                // Check if user already exists
                if (localStorage.getItem(`user_${phone}`)) {
                    alert('User already exists with this phone number. Please login.');
                    showLoginForm();
                    return;
                }

                // Create new user
                currentUser = {
                    phone: phone,
                    name: fullName,
                    email: email,
                    initial: fullName.charAt(0).toUpperCase(),
                    joinDate: new Date().toISOString(),
                    earnings: {
                        total: 0,
                        available: 0,
                        withdrawn: 0,
                        thisMonth: 0,
                        autoPaid: 0
                    },
                    sales: 0,
                    withdrawals: [],
                    autoWithdrawal: true,
                    autoMethod: 'upi',
                    autoUpiId: 'user@ybl',
                    referralCode: referralCode
                };

                // Save user
                saveUserData();
                updateUserInterface();
                loadUserData();
                closeModal('loginModal');
                
                // Reset form
                document.getElementById('signupForm').reset();
                
                alert('Account created successfully! Welcome to SkillPixo 🎉\n\nYou can now start earning 75% commission on course sales!');
            } else {
                alert('Please enter a valid 10-digit Indian phone number');
            }
        }

        function setupOtpInputs() {
            const otpInputs = document.querySelectorAll('.otp-input');
            otpInputs.forEach((input, index) => {
                input.addEventListener('input', (e) => {
                    if (e.target.value.length === 1 && index < otpInputs.length - 1) {
                        otpInputs[index + 1].focus();
                    }
                });
                
                input.addEventListener('keydown', (e) => {
                    if (e.key === 'Backspace' && !e.target.value && index > 0) {
                        otpInputs[index - 1].focus();
                    }
                });
            });
        }

        function initializeAutoWithdrawal() {
            // Load auto withdrawal settings
            const autoSettings = JSON.parse(localStorage.getItem('autoWithdrawalSettings') || '{}');
            
            // Set default day to Monday if not set
            if (!autoSettings.payoutDay) {
                autoSettings.payoutDay = 1; // Monday
                localStorage.setItem('autoWithdrawalSettings', JSON.stringify(autoSettings));
            }
            
            // Update admin dropdown
            document.getElementById('adminPayoutDay').value = autoSettings.payoutDay;
            
            // Start auto payout check
            checkAutoPayout();
        }

        function startCountdownTimer() {
            function updateCountdown() {
                const now = new Date();
                const nextMonday = getNextPayoutDate();
                const diff = nextMonday - now;

                if (diff > 0) {
                    const days = Math.floor(diff / (1000 * 60 * 60 * 24));
                    const hours = Math.floor((diff % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
                    const minutes = Math.floor((diff % (1000 * 60 * 60)) / (1000 * 60));
                    const seconds = Math.floor((diff % (1000 * 60)) / 1000);

                    document.getElementById('countdownDays').textContent = days.toString().padStart(2, '0');
                    document.getElementById('countdownHours').textContent = hours.toString().padStart(2, '0');
                    document.getElementById('countdownMinutes').textContent = minutes.toString().padStart(2, '0');
                    document.getElementById('countdownSeconds').textContent = seconds.toString().padStart(2, '0');

                    // Update next payout date
                    document.getElementById('nextPayoutDate').textContent = nextMonday.toLocaleDateString();
                }
            }

            updateCountdown();
            setInterval(updateCountdown, 1000);
        }

        function getNextPayoutDate() {
            const autoSettings = JSON.parse(localStorage.getItem('autoWithdrawalSettings') || '{}');
            const payoutDay = autoSettings.payoutDay || 1; // Default Monday
            
            const now = new Date();
            const result = new Date(now);
            
            // Find next payout day (Monday = 1, Sunday = 0 in getDay())
            const currentDay = now.getDay() || 7; // Convert Sunday (0) to 7
            let daysUntilPayout = payoutDay - currentDay;
            
            if (daysUntilPayout < 0) {
                daysUntilPayout += 7;
            } else if (daysUntilPayout === 0) {
                // If today is payout day but time has passed, schedule for next week
                const payoutTime = new Date(now);
                payoutTime.setHours(10, 0, 0, 0); // 10:00 AM
                
                if (now > payoutTime) {
                    daysUntilPayout = 7;
                }
            }
            
            result.setDate(now.getDate() + daysUntilPayout);
            result.setHours(10, 0, 0, 0); // Set to 10:00 AM
            
            return result;
        }

        function checkAutoPayout() {
            const now = new Date();
            const nextPayout = getNextPayoutDate();
            
            // Check if it's time for auto payout
            if (now >= nextPayout) {
                processAutoPayout();
                
                // Schedule next payout for next week
                const autoSettings = JSON.parse(localStorage.getItem('autoWithdrawalSettings') || '{}');
                autoSettings.lastPayout = new Date().toISOString();
                localStorage.setItem('autoWithdrawalSettings', JSON.stringify(autoSettings));
            }
        }

        function processAutoPayout() {
            const users = getAllUsers();
            let totalPaid = 0;
            
            users.forEach(user => {
                // Check if user has auto withdrawal enabled and sufficient balance
                const autoEnabled = user.autoWithdrawal !== false; // Default enabled
                const minAmount = 100; // Minimum payout amount
                
                if (autoEnabled && user.earnings.available >= minAmount) {
                    // Create auto withdrawal
                    const withdrawal = {
                        id: Date.now() + Math.random(),
                        amount: user.earnings.available,
                        method: user.autoMethod || 'upi',
                        date: new Date().toISOString(),
                        status: 'paid',
                        userPhone: user.phone,
                        userName: user.name,
                        type: 'auto'
                    };
                    
                    // Update user balance
                    user.earnings.withdrawn += user.earnings.available;
                    user.earnings.available = 0;
                    user.withdrawals = user.withdrawals || [];
                    user.withdrawals.push(withdrawal);
                    
                    // Save user
                    localStorage.setItem(`user_${user.phone}`, JSON.stringify(user));
                    
                    totalPaid += withdrawal.amount;
                    
                    // Add to platform withdrawals
                    const withdrawals = JSON.parse(localStorage.getItem('withdrawalRequests') || '[]');
                    withdrawals.push(withdrawal);
                    localStorage.setItem('withdrawalRequests', JSON.stringify(withdrawals));
                }
            });
            
            if (totalPaid > 0) {
                console.log(`Auto payout completed: ₹${totalPaid} distributed to ${users.length} users`);
            }
        }

        function runAutoPayoutNow() {
            if (confirm('Run auto payout for all eligible users now?')) {
                processAutoPayout();
                alert('Auto payout completed successfully!');
                loadAdminData();
            }
        }

        function updateAutoPayoutDay() {
            const payoutDay = document.getElementById('adminPayoutDay').value;
            const autoSettings = JSON.parse(localStorage.getItem('autoWithdrawalSettings') || '{}');
            autoSettings.payoutDay = parseInt(payoutDay);
            localStorage.setItem('autoWithdrawalSettings', JSON.stringify(autoSettings));
            alert('Auto payout day updated successfully!');
        }

        function toggleAutoWithdrawal() {
            if (!currentUser) return;
            
            const enabled = document.getElementById('autoWithdrawalToggle').checked;
            currentUser.autoWithdrawal = enabled;
            saveUserData();
            
            if (enabled) {
                alert('Auto withdrawal enabled! You will receive payments automatically every week.');
            } else {
                alert('Auto withdrawal disabled. You need to manually withdraw your earnings.');
            }
        }

        function selectAutoWithdrawalMethod(method) {
            selectedAutoWithdrawalMethod = method;
            
            // Update UI
            document.querySelectorAll('.withdrawal-option').forEach(option => {
                option.classList.remove('selected');
            });
            event.currentTarget.classList.add('selected');
            
            // Save to user preferences
            if (currentUser) {
                currentUser.autoMethod = method;
                saveUserData();
            }
        }

        function saveAutoWithdrawalSettings() {
            if (!currentUser) {
                alert('Please login to save settings');
                return;
            }
            
            const upiId = document.getElementById('autoUpiId').value;
            if (!upiId) {
                alert('Please enter your UPI ID');
                return;
            }
            
            currentUser.autoUpiId = upiId;
            currentUser.autoWithdrawal = document.getElementById('autoWithdrawalToggle').checked;
            currentUser.autoMethod = selectedAutoWithdrawalMethod;
            
            saveUserData();
            alert('Auto withdrawal settings saved successfully!');
        }

        function handleLogin(e) {
            e.preventDefault();
            const phone = document.getElementById('phoneNumber').value;
            
            if (phone.length === 10 && /^[6-9]\d{9}$/.test(phone)) {
                // Check if user exists
                if (!localStorage.getItem(`user_${phone}`)) {
                    alert('No account found with this phone number. Please sign up first.');
                    showSignupForm();
                    return;
                }

                // Generate OTP
                otp = '1234'; // For demo, always use 1234
                
                // Show OTP section
                document.getElementById('otpContainer').style.display = 'block';
                document.getElementById('phoneLoginForm').style.display = 'none';
                
                // Auto-focus first OTP input
                setTimeout(() => {
                    document.querySelector('.otp-input').focus();
                }, 100);
            } else {
                alert('Please enter a valid 10-digit Indian phone number');
            }
        }

        function verifyOtp() {
            const inputs = document.querySelectorAll('.otp-input');
            const enteredOtp = Array.from(inputs).map(input => input.value).join('');
            
            if (enteredOtp === otp) {
                const phone = document.getElementById('phoneNumber').value;
                
                // Load user
                currentUser = getUserData(phone);
                
                // Save user
                saveUserData();
                updateUserInterface();
                loadUserData();
                closeModal('loginModal');
                
                // Reset form
                document.getElementById('otpContainer').style.display = 'none';
                document.getElementById('phoneLoginForm').style.display = 'block';
                document.getElementById('phoneNumber').value = '';
                inputs.forEach(input => input.value = '');
                
                alert('Login successful! Welcome back to SkillPixo 🎉');
            } else {
                alert('Invalid OTP. Please try again.');
            }
        }

        function getUserData(phone) {
            const savedData = localStorage.getItem(`user_${phone}`);
            if (savedData) {
                return JSON.parse(savedData);
            }
            
            return {
                phone: phone,
                name: `User${phone.slice(-4)}`,
                initial: 'U',
                joinDate: '',
                earnings: {
                    total: 0,
                    available: 0,
                    withdrawn: 0,
                    thisMonth: 0,
                    autoPaid: 0
                },
                sales: 0,
                withdrawals: [],
                autoWithdrawal: true,
                autoMethod: 'upi',
                autoUpiId: 'user@ybl'
            };
        }

        function saveUserData() {
            localStorage.setItem(`user_${currentUser.phone}`, JSON.stringify(currentUser));
            localStorage.setItem('currentUser', JSON.stringify(currentUser));
        }

        function updateUserInterface() {
            if (currentUser) {
                document.getElementById('loginBtn').style.display = 'none';
                document.getElementById('userDashboard').style.display = 'flex';
                document.getElementById('userName').textContent = currentUser.name;
                document.getElementById('userAvatar').textContent = currentUser.initial;
                
                // Update auto withdrawal settings
                document.getElementById('autoWithdrawalToggle').checked = currentUser.autoWithdrawal !== false;
                document.getElementById('autoUpiId').value = currentUser.autoUpiId || '';
                
                // Show admin button if user is CEO
                if (currentUser.phone === ADMIN_PHONE) {
                    document.getElementById('adminBtn').style.display = 'block';
                }
            } else {
                document.getElementById('loginBtn').style.display = 'block';
                document.getElementById('userDashboard').style.display = 'none';
                document.getElementById('adminBtn').style.display = 'none';
            }
        }

        function loadUserData() {
            if (!currentUser) return;
            
            // Update earnings display
            document.getElementById('totalEarnings').textContent = currentUser.earnings.total;
            document.getElementById('totalSales').textContent = currentUser.sales;
            document.getElementById('thisMonthEarnings').textContent = currentUser.earnings.thisMonth;
            document.getElementById('availableBalance').textContent = currentUser.earnings.available;
            document.getElementById('withdrawBalance').textContent = currentUser.earnings.available;
            document.getElementById('nextPayoutAmount').textContent = currentUser.earnings.available;
            document.getElementById('totalAutoPaid').textContent = currentUser.earnings.autoPaid || 0;
            
            // Load withdrawal history
            loadWithdrawalHistory();
            
            // Load admin data if admin
            if (currentUser.phone === ADMIN_PHONE) {
                loadAdminData();
            }
        }

        function loadWithdrawalHistory() {
            const historyContainer = document.getElementById('withdrawalHistory');
            const withdrawals = currentUser.withdrawals || [];
            
            if (withdrawals.length === 0) {
                historyContainer.innerHTML = '<p>No withdrawal history found.</p>';
                return;
            }
            
            historyContainer.innerHTML = withdrawals.map(withdrawal => `
                <div class="withdrawal-item">
                    <div>
                        <strong>₹${withdrawal.amount}</strong>
                        <div>${withdrawal.method.toUpperCase()} • ${new Date(withdrawal.date).toLocaleDateString()}</div>
                        ${withdrawal.type === 'auto' ? '<small style="color: #06D6A0;">Auto Payout</small>' : ''}
                    </div>
                    <div class="withdrawal-status status-${withdrawal.status}">
                        ${withdrawal.status.charAt(0).toUpperCase() + withdrawal.status.slice(1)}
                    </div>
                </div>
            `).join('');
        }

        // Admin Functions
        function showAdminPanel() {
            document.querySelectorAll('section').forEach(section => {
                section.style.display = 'none';
            });
            document.getElementById('adminPanel').style.display = 'block';
            loadAdminData();
        }

        function loadAdminData() {
            if (currentUser.phone !== ADMIN_PHONE) return;
            
            const platformEarnings = parseFloat(localStorage.getItem('platformEarnings') || '0');
            const adminEarnings = parseFloat(localStorage.getItem('adminEarnings') || '0');
            const users = getAllUsers();
            const withdrawals = JSON.parse(localStorage.getItem('withdrawalRequests') || '[]');
            
            document.getElementById('totalPlatformEarnings').textContent = platformEarnings;
            document.getElementById('totalUsers').textContent = users.length;
            document.getElementById('totalWithdrawals').textContent = withdrawals.length;
            document.getElementById('adminBalance').textContent = adminEarnings;
            document.getElementById('adminWithdrawBalance').textContent = adminEarnings;
            document.getElementById('adminAvailableBalance').textContent = adminEarnings;
            
            loadAdminWithdrawalTable();
        }

        function getAllUsers() {
            const users = [];
            for (let i = 0; i < localStorage.length; i++) {
                const key = localStorage.key(i);
                if (key.startsWith('user_') && key !== 'user_undefined') {
                    const user = JSON.parse(localStorage.getItem(key));
                    users.push(user);
                }
            }
            return users;
        }

        function loadAdminWithdrawalTable() {
            const table = document.getElementById('adminWithdrawalTable');
            const withdrawals = JSON.parse(localStorage.getItem('withdrawalRequests') || '[]');
            
            if (withdrawals.length === 0) {
                table.innerHTML = '<tr><td colspan="6" style="text-align: center;">No withdrawal requests</td></tr>';
                return;
            }
            
            table.innerHTML = withdrawals.map(withdrawal => `
                <tr>
                    <td>${withdrawal.userName}<br><small>${withdrawal.userPhone}</small></td>
                    <td>₹${withdrawal.amount}</td>
                    <td>${withdrawal.method.toUpperCase()}</td>
                    <td>${new Date(withdrawal.date).toLocaleDateString()}</td>
                    <td>
                        <span class="withdrawal-status status-${withdrawal.status}">
                            ${withdrawal.status.charAt(0).toUpperCase() + withdrawal.status.slice(1)}
                        </span>
                    </td>
                    <td>${withdrawal.type === 'auto' ? 'Auto' : 'Manual'}</td>
                    <td>
                        ${withdrawal.status === 'pending' ? `
                            <button class="action-btn approve-btn" onclick="updateWithdrawalStatus(${withdrawal.id}, 'approved')">Approve</button>
                            <button class="action-btn reject-btn" onclick="updateWithdrawalStatus(${withdrawal.id}, 'rejected')">Reject</button>
                        ` : withdrawal.status === 'approved' ? `
                            <button class="action-btn pay-btn" onclick="updateWithdrawalStatus(${withdrawal.id}, 'paid')">Mark Paid</button>
                        ` : ''}
                    </td>
                </tr>
            `).join('');
        }

        function updateWithdrawalStatus(id, status) {
            const withdrawals = JSON.parse(localStorage.getItem('withdrawalRequests') || '[]');
            const withdrawal = withdrawals.find(w => w.id === id);
            
            if (withdrawal) {
                withdrawal.status = status;
                withdrawal.processedDate = new Date().toISOString();
                
                // Update user's withdrawal status
                const user = getUserData(withdrawal.userPhone);
                if (user.withdrawals) {
                    const userWithdrawal = user.withdrawals.find(w => w.id === id);
                    if (userWithdrawal) {
                        userWithdrawal.status = status;
                        localStorage.setItem(`user_${user.phone}`, JSON.stringify(user));
                    }
                }
                
                localStorage.setItem('withdrawalRequests', JSON.stringify(withdrawals));
                loadAdminWithdrawalTable();
                
                alert(`Withdrawal ${status} successfully!`);
            }
        }

        function showAdminWithdrawal() {
            showModal('adminWithdrawalModal');
        }

        function processAdminWithdrawal() {
            const amount = parseFloat(document.getElementById('adminWithdrawAmount').value);
            const adminEarnings = parseFloat(localStorage.getItem('adminEarnings') || '0');
            
            if (amount > adminEarnings) {
                alert('Insufficient admin balance');
                return;
            }
            
            // Update admin earnings
            localStorage.setItem('adminEarnings', (adminEarnings - amount).toString());
            
            closeModal('adminWithdrawalModal');
            loadAdminData();
            
            alert(`Admin withdrawal of ₹${amount} processed successfully!`);
        }

        // Utility Functions
        function showModal(modalId) {
            document.getElementById(modalId).style.display = 'block';
        }

        function closeModal(modalId) {
            document.getElementById(modalId).style.display = 'none';
        }

        function showCoursesSection() {
            document.getElementById('courses').scrollIntoView({ behavior: 'smooth' });
        }

        function showWithdrawalSection() {
            if (!currentUser) {
                alert('Please login to withdraw earnings');
                showModal('loginModal');
                return;
            }
            
            if (currentUser.earnings.available < 100) {
                alert('Minimum ₹100 required for withdrawal');
                return;
            }
            
            document.getElementById('withdrawal').scrollIntoView({ behavior: 'smooth' });
        }

        // Course Functions
        function showCourseDetails(courseId) {
            const course = courses[courseId];
            const commission = course.price * course.commission;
            alert(`Course: ${course.title}\nPrice: ₹${course.price}\nYour Commission: ${course.commission * 100}% (₹${commission})`);
        }

        function getAffiliateLink(courseId) {
            if (!currentUser) {
                alert('Please login to get affiliate link');
                showModal('loginModal');
                return;
            }
            
            const course = courses[courseId];
            const affiliateLink = `https://skillpixo.com/course/${courseId}?ref=${currentUser.phone}`;
            const commission = course.price * course.commission;
            
            // Copy to clipboard
            navigator.clipboard.writeText(affiliateLink).then(() => {
                alert(`Affiliate link copied to clipboard!\n\n${affiliateLink}\n\nShare this link to earn 75% commission (₹${commission}) on each sale!`);
            });
        }

        // Withdrawal Functions
        function selectWithdrawalMethod(method) {
            selectedWithdrawalMethod = method;
            
            // Hide all method details
            document.getElementById('upiDetails').style.display = 'none';
            document.getElementById('bankDetails').style.display = 'none';
            document.getElementById('paytmDetails').style.display = 'none';
            
            // Show selected method details
            if (method === 'upi') {
                document.getElementById('upiDetails').style.display = 'block';
            } else if (method === 'bank') {
                document.getElementById('bankDetails').style.display = 'block';
            } else if (method === 'paytm') {
                document.getElementById('paytmDetails').style.display = 'block';
            }
            
            // Update UI
            document.querySelectorAll('.withdrawal-option').forEach(option => {
                option.classList.remove('selected');
            });
            event.currentTarget.classList.add('selected');
        }

        function handleWithdrawal(e) {
            e.preventDefault();
            
            if (!currentUser) {
                alert('Please login to withdraw earnings');
                showModal('loginModal');
                return;
            }
            
            const amount = parseFloat(document.getElementById('withdrawAmount').value);
            
            if (amount < 100) {
                alert('Minimum withdrawal amount is ₹100');
                return;
            }
            
            if (amount > currentUser.earnings.available) {
                alert('Insufficient balance');
                return;
            }
            
            if (!selectedWithdrawalMethod) {
                alert('Please select a withdrawal method');
                return;
            }
            
            // Create withdrawal request
            const withdrawal = {
                id: Date.now(),
                amount: amount,
                method: selectedWithdrawalMethod,
                date: new Date().toISOString(),
                status: 'pending',
                type: 'manual'
            };
            
            // Update user balance
            currentUser.earnings.available -= amount;
            currentUser.withdrawals = currentUser.withdrawals || [];
            currentUser.withdrawals.unshift(withdrawal);
            
            // Save user data
            saveUserData();
            
            // Add to platform withdrawals
            const withdrawals = JSON.parse(localStorage.getItem('withdrawalRequests') || '[]');
            withdrawal.userPhone = currentUser.phone;
            withdrawal.userName = currentUser.name;
            withdrawals.unshift(withdrawal);
            localStorage.setItem('withdrawalRequests', JSON.stringify(withdrawals));
            
            // Update UI
            loadUserData();
            
            // Reset form
            document.getElementById('withdrawalForm').reset();
            document.querySelectorAll('.withdrawal-option').forEach(option => {
                option.classList.remove('selected');
            });
            document.getElementById('upiDetails').style.display = 'none';
            document.getElementById('bankDetails').style.display = 'none';
            document.getElementById('paytmDetails').style.display = 'none';
            
            alert(`Withdrawal request of ₹${amount} submitted successfully!`);
        }

        function handleLogout() {
            currentUser = null;
            localStorage.removeItem('currentUser');
            updateUserInterface();
            alert('Logged out successfully!');
        }

        // Close modals when clicking outside
        window.onclick = function(event) {
            if (event.target.classList.contains('modal')) {
                event.target.style.display = 'none';
            }
        }

        // Simulate some initial data for demo
        function simulateInitialData() {
            if (!localStorage.getItem('demoDataCreated')) {
                const demoUser = {
                    phone: '9876543210',
                    name: 'Demo User',
                    initial: 'D',
                    joinDate: new Date().toISOString(),
                    earnings: {
                        total: 2845,
                        available: 845,
                        withdrawn: 2000,
                        thisMonth: 845,
                        autoPaid: 1500
                    },
                    sales: 18,
                    withdrawals: [
                        {
                            id: 1,
                            amount: 500,
                            method: 'upi',
                            date: new Date(Date.now() - 7 * 24 * 60 * 60 * 1000).toISOString(),
                            status: 'paid',
                            type: 'auto'
                        },
                        {
                            id: 2,
                            amount: 1500,
                            method: 'bank',
                            date: new Date(Date.now() - 14 * 24 * 60 * 60 * 1000).toISOString(),
                            status: 'paid',
                            type: 'manual'
                        }
                    ],
                    autoWithdrawal: true,
                    autoMethod: 'upi',
                    autoUpiId: 'demo@ybl'
                };
                
                localStorage.setItem('user_9876543210', JSON.stringify(demoUser));
                localStorage.setItem('demoDataCreated', 'true');
            }
        }

        // Run demo data simulation
        simulateInitialData();
    </script>
</body>
</html>A
