<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>产业大脑区域经济综合服务平台</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'PingFang SC', 'Microsoft YaHei', '微软雅黑', 'Helvetica Neue', Arial, sans-serif;
            line-height: 1.6;
            color: #333;
            background: #fff;
            overflow-x: hidden;
        }
        
        /* 顶部公告栏 */
        .top-notice {
            background: linear-gradient(135deg, #0066cc 0%, #004499 100%);
            color: white;
            text-align: center;
            padding: 8px 0;
            font-size: 13px;
            position: relative;
            overflow: hidden;
        }
        
        .top-notice::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.1), transparent);
            animation: shimmer 3s infinite;
        }
        
        @keyframes shimmer {
            0% { left: -100%; }
            100% { left: 100%; }
        }
        
        .notice-content {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
            position: relative;
            z-index: 1;
        }
        
        /* 顶部导航 */
        .header {
            background: #fff;
            box-shadow: 0 2px 20px rgba(0,0,0,0.06);
            position: sticky;
            top: 0;
            z-index: 1000;
            border-bottom: 1px solid #e8eaed;
        }
        
        .header-content {
            max-width: 1600px;
            margin: 0 auto;
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 0 40px;
            height: 90px;
        }
        
        .logo-section {
            display: flex;
            align-items: center;
            gap: 20px;
            flex: 0 0 auto;
            max-width: 400px;
        }
        
        .logo {
            width: 60px;
            height: 60px;
            background: linear-gradient(135deg, #0066cc 0%, #004499 100%);
            border-radius: 14px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 24px;
            color: #fff;
            font-weight: 700;
            box-shadow: 0 4px 15px rgba(0,102,204,0.3);
            flex-shrink: 0;
        }
        
        .platform-name {
            font-size: 22px;
            font-weight: 600;
            color: #1a1a1a;
            letter-spacing: 0.5px;
            line-height: 1.3;
            overflow: hidden;
            text-overflow: ellipsis;
            white-space: nowrap;
        }
        
        .platform-name .sub {
            font-size: 14px;
            color: #666;
            font-weight: 400;
            display: block;
            margin-top: 3px;
            overflow: hidden;
            text-overflow: ellipsis;
            white-space: nowrap;
        }
        
        .main-nav {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            grid-template-rows: repeat(2, 1fr);
            gap: 1px;
            flex: 1;
            max-width: 480px;
            margin: 0 3px;
        }
        
        .nav-item {
            padding: 6px 4px;
            cursor: pointer;
            color: #374151;
            font-size: 12px;
            font-weight: 500;
            text-align: center;
            white-space: nowrap;
            min-width: 50px;
            background: transparent;
            border: none;
        }
        
        .nav-item:hover {
            color: #374151;
        }
        
        .nav-item.active {
            color: #0066cc;
            font-weight: 600;
        }
        
        .user-section {
            display: flex;
            gap: 12px;
            align-items: center;
            flex: 0 0 auto;
            max-width: 300px;
        }
        
        .nav-item {
            padding: 18px 16px;
            cursor: pointer;
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            color: #374151;
            font-size: 15px;
            font-weight: 500;
            position: relative;
            border-radius: 8px;
            text-align: center;
            margin: 2px;
            background: transparent;
            border: 1px solid transparent;
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
        }
        
        .nav-item:hover {
            background: rgba(255, 255, 255, 0.9);
            color: #0066cc;
            transform: translateY(-1px);
            box-shadow: 0 2px 8px rgba(0, 102, 204, 0.15);
            border-color: rgba(0, 102, 204, 0.2);
        }
        
        .nav-item.active {
            background: linear-gradient(135deg, #0066cc 0%, #3d8bff 100%);
            color: white;
            box-shadow: 0 4px 12px rgba(0, 102, 204, 0.25);
        }
        
        .nav-item.active:hover {
            background: linear-gradient(135deg, #0052a3 0%, #0066cc 100%);
            color: white;
            transform: translateY(-2px);
            box-shadow: 0 6px 16px rgba(0, 102, 204, 0.35);
        }
        
        .nav-item::after {
            display: none;
        }
        
        .user-section {
            display: flex;
            gap: 16px;
            align-items: center;
            width: 320px;
            justify-content: flex-end;
            flex-shrink: 0;
        }
        
        .login-btn {
            padding: 10px 18px;
            border: 1px solid #d1d5db;
            background: #fff;
            color: #374151;
            border-radius: 6px;
            cursor: pointer;
            transition: all 0.3s ease;
            font-size: 13px;
            font-weight: 500;
            white-space: nowrap;
            min-width: 70px;
        }
        
        .login-btn::before {
            display: none;
        }
        
        .login-btn:hover {
            border-color: #0066cc;
            color: #0066cc;
            box-shadow: 0 2px 8px rgba(0,102,204,0.15);
        }
        
        .login-btn.primary {
            background: linear-gradient(135deg, #0066cc 0%, #3d8bff 100%);
            color: white;
            border-color: #0066cc;
            box-shadow: 0 2px 10px rgba(0,102,204,0.2);
        }
        
        /* 移动端优化 - 汉堡菜单 */
        .mobile-menu-toggle {
            display: none;
            flex-direction: column;
            cursor: pointer;
            padding: 10px;
            background: rgba(248, 250, 252, 0.9);
            border-radius: 8px;
            border: 1px solid rgba(229, 231, 235, 0.5);
            z-index: 1001;
            position: relative;
            min-width: 44px;
            min-height: 44px;
            justify-content: center;
            align-items: center;
            gap: 3px;
        }
        
        .mobile-menu-toggle span {
            width: 22px;
            height: 3px;
            background: #374151;
            border-radius: 2px;
            transition: all 0.3s ease;
            display: block;
        }
        
        .mobile-menu-toggle.active span:nth-child(1) {
            transform: rotate(45deg) translate(5px, 5px);
        }
        
        .mobile-menu-toggle.active span:nth-child(2) {
            opacity: 0;
            transform: scale(0);
        }
        
        .mobile-menu-toggle.active span:nth-child(3) {
            transform: rotate(-45deg) translate(7px, -6px);
        }
        
        .mobile-nav {
            display: none;
            position: absolute;
            top: 100%;
            left: 0;
            right: 0;
            background: white;
            box-shadow: 0 8px 32px rgba(0,0,0,0.15);
            border-top: 1px solid #e5e7eb;
            z-index: 1000;
            max-height: 0;
            overflow: hidden;
            transition: all 0.3s ease;
        }
        
        .mobile-nav.active {
            display: block;
            max-height: 500px;
            animation: slideDown 0.3s ease;
        }
        
        @keyframes slideDown {
            from {
                opacity: 0;
                transform: translateY(-10px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }
        
        .mobile-nav-item {
            display: block;
            padding: 16px 24px;
            color: #374151;
            font-size: 15px;
            font-weight: 500;
            border-bottom: 1px solid #f3f4f6;
            cursor: pointer;
            transition: all 0.3s ease;
            position: relative;
            user-select: none;
            -webkit-tap-highlight-color: transparent;
        }
        
        .mobile-nav-item:active {
            background-color: #f0f9ff;
        }
        
        .mobile-nav-item:hover {
            background-color: #f8f9fa;
            color: #0066cc;
        }
        
        .mobile-nav-item.active {
            color: #0066cc;
            font-weight: 600;
            background-color: #eff6ff;
        }
        
        .mobile-nav-item:last-child {
            border-bottom: none;
        }
        
        .mobile-nav-divider {
            border-top: 2px solid #e5e7eb;
            padding-top: 12px;
            margin-top: 8px;
            background-color: #f8f9fa;
        }
        
        /* 增强所有可点击元素的样式 */
        .stat-item,
        .data-item,
        .case-card,
        .advantage-card,
        .service-card,
        .news-item {
            cursor: pointer;
            user-select: none;
            -webkit-tap-highlight-color: transparent;
        }
        
        .stat-item:hover,
        .data-item:hover {
            transform: translateY(-2px);
            box-shadow: 0 4px 15px rgba(0,102,204,0.15);
        }
        
        .news-item:hover {
            transform: translateX(5px);
        }
        
        .quick-links a,
        .footer-section a,
        .footer-links a {
            cursor: pointer;
            user-select: none;
            -webkit-tap-highlight-color: transparent;
        }
        
        /* 按钮点击反馈 */
        .login-btn:active,
        .cta-btn:active,
        .action-btn:active,
        .service-btn:active {
            transform: scale(0.98);
        }
        
        /* 卡片点击反馈 */
        .stat-item:active,
        .data-item:active,
        .case-card:active,
        .advantage-card:active,
        .service-card:active {
            transform: scale(0.99);
        }
        
        /* 新闻标签样式增强 */
        .news-tab {
            cursor: pointer;
            user-select: none;
            -webkit-tap-highlight-color: transparent;
        }
        
        .news-tab:active {
            transform: scale(0.98);
        }
        
        /* 核心价值展示区 */
        .hero-section {
            background: linear-gradient(135deg, #f8fafc 0%, #e2e8f0 100%);
            position: relative;
            overflow: hidden;
            padding: 0;
        }
        
        .hero-section::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100"><defs><pattern id="grid" width="20" height="20" patternUnits="userSpaceOnUse"><path d="M 20 0 L 0 0 0 20" fill="none" stroke="%23e2e8f0" stroke-width="0.5" opacity="0.3"/></pattern></defs><rect width="100" height="100" fill="url(%23grid)"/></svg>');
        }
        
        .hero-content {
            max-width: 1600px;
            margin: 0 auto;
            padding: 100px 40px;
            position: relative;
            z-index: 2;
            display: grid;
            grid-template-columns: 1fr 450px;
            gap: 80px;
            align-items: center;
        }
        
        .hero-text {
            color: #1a1a1a;
        }
        
        .hero-title {
            font-size: 36px;
            font-weight: 700;
            margin-bottom: 24px;
            line-height: 1.3;
            background: linear-gradient(135deg, #1a1a1a 0%, #0066cc 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }
        
        .hero-subtitle {
            font-size: 16px;
            color: #4b5563;
            margin-bottom: 40px;
            line-height: 1.8;
            max-width: 500px;
        }
        
        .hero-features {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 20px;
            margin-bottom: 40px;
        }
        
        .feature-item {
            display: flex;
            align-items: center;
            gap: 12px;
            font-size: 14px;
            color: #374151;
        }
        
        .feature-icon {
            width: 20px;
            height: 20px;
            background: linear-gradient(135deg, #0066cc 0%, #3d8bff 100%);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 10px;
            flex-shrink: 0;
        }
        
        .hero-cta {
            display: flex;
            gap: 16px;
        }
        
        .cta-btn {
            padding: 14px 28px;
            border-radius: 8px;
            text-decoration: none;
            font-weight: 600;
            font-size: 15px;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }
        
        .cta-btn.primary {
            background: linear-gradient(135deg, #0066cc 0%, #3d8bff 100%);
            color: white;
            box-shadow: 0 4px 15px rgba(0,102,204,0.25);
        }
        
        .cta-btn.primary:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 25px rgba(0,102,204,0.35);
        }
        
        .cta-btn.secondary {
            background: white;
            color: #0066cc;
            border: 2px solid #0066cc;
        }
        
        .cta-btn.secondary:hover {
            background: #0066cc;
            color: white;
        }
        
        .hero-visual {
            position: relative;
        }
        
        .stats-dashboard {
            background: white;
            border-radius: 16px;
            padding: 32px;
            box-shadow: 0 20px 60px rgba(0,0,0,0.08);
            border: 1px solid #e5e7eb;
            position: relative;
        }
        
        .stats-dashboard::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 4px;
            background: linear-gradient(90deg, #0066cc, #3d8bff, #66a3ff);
            border-radius: 16px 16px 0 0;
        }
        
        .dashboard-title {
            font-size: 18px;
            font-weight: 600;
            color: #1a1a1a;
            margin-bottom: 24px;
            text-align: center;
        }
        
        .stats-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 24px;
        }
        
        .stat-item {
            text-align: center;
            padding: 20px;
            background: #f8fafc;
            border-radius: 12px;
            border: 1px solid #e5e7eb;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }
        
        .stat-item::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 2px;
            background: linear-gradient(90deg, #0066cc, #3d8bff);
            transform: scaleX(0);
            transition: transform 0.3s ease;
        }
        
        .stat-item:hover::before {
            transform: scaleX(1);
        }
        
        .stat-item:hover {
            background: white;
            box-shadow: 0 4px 15px rgba(0,102,204,0.1);
        }
        
        .stat-number {
            font-size: 28px;
            font-weight: 700;
            color: #0066cc;
            display: block;
            margin-bottom: 8px;
            font-family: 'SF Mono', 'Monaco', monospace;
        }
        
        .stat-label {
            font-size: 13px;
            color: #6b7280;
            font-weight: 500;
        }
        
        /* 主要内容区域 */
        .main-content {
            max-width: 1600px;
            margin: 0 auto;
            padding: 80px 40px;
        }
        
        .section {
            margin-bottom: 80px;
        }
        
        .section-header {
            text-align: center;
            margin-bottom: 60px;
        }
        
        .section-title {
            font-size: 32px;
            font-weight: 700;
            color: #1a1a1a;
            margin-bottom: 16px;
            position: relative;
        }
        
        .section-subtitle {
            font-size: 16px;
            color: #6b7280;
            max-width: 600px;
            margin: 0 auto;
            line-height: 1.6;
        }
        
        .section-title::after {
            content: '';
            position: absolute;
            bottom: -12px;
            left: 50%;
            transform: translateX(-50%);
            width: 60px;
            height: 4px;
            background: linear-gradient(90deg, #0066cc, #3d8bff);
            border-radius: 2px;
        }
        
        /* 服务模块网格 */
        .services-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(380px, 1fr));
            gap: 32px;
        }
        
        .service-card {
            background: white;
            border-radius: 16px;
            padding: 36px;
            box-shadow: 0 4px 20px rgba(0,0,0,0.04);
            border: 1px solid #e5e7eb;
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
            position: relative;
            overflow: hidden;
        }
        
        .service-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 4px;
            background: linear-gradient(90deg, #0066cc, #3d8bff);
            transform: scaleX(0);
            transition: transform 0.4s ease;
        }
        
        .service-card:hover::before {
            transform: scaleX(1);
        }
        
        .service-card:hover {
            transform: translateY(-8px);
            box-shadow: 0 20px 40px rgba(0,102,204,0.12);
            border-color: #d1d5db;
        }
        
        .service-header {
            display: flex;
            align-items: center;
            gap: 16px;
            margin-bottom: 24px;
        }
        
        .service-icon {
            width: 56px;
            height: 56px;
            background: linear-gradient(135deg, #0066cc 0%, #3d8bff 100%);
            border-radius: 14px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 24px;
            flex-shrink: 0;
            box-shadow: 0 4px 15px rgba(0,102,204,0.2);
            position: relative;
        }
        
        .service-icon::before {
            content: '';
            position: absolute;
            top: 4px;
            left: 4px;
            right: 4px;
            bottom: 4px;
            border: 1px solid rgba(255,255,255,0.3);
            border-radius: 10px;
        }
        
        .service-title {
            font-size: 20px;
            font-weight: 600;
            color: #1a1a1a;
            margin-bottom: 4px;
        }
        
        .service-tag {
            background: #eff6ff;
            color: #0066cc;
            padding: 4px 12px;
            border-radius: 20px;
            font-size: 12px;
            font-weight: 500;
            display: inline-block;
        }
        
        .service-description {
            color: #4b5563;
            margin-bottom: 24px;
            line-height: 1.7;
            font-size: 15px;
        }
        
        .service-features {
            margin-bottom: 28px;
        }
        
        .service-features li {
            color: #374151;
            margin-bottom: 10px;
            padding-left: 24px;
            position: relative;
            font-size: 14px;
            line-height: 1.5;
        }
        
        .service-features li::before {
            content: '✓';
            position: absolute;
            left: 0;
            color: #10b981;
            font-weight: bold;
            width: 16px;
            height: 16px;
            background: #ecfdf5;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 10px;
            top: 2px;
        }
        
        .service-buttons {
            display: flex;
            gap: 12px;
        }
        
        .service-btn {
            padding: 12px 24px;
            border-radius: 8px;
            text-decoration: none;
            font-size: 14px;
            font-weight: 600;
            transition: all 0.3s ease;
            text-align: center;
            flex: 1;
            position: relative;
            overflow: hidden;
        }
        
        .service-btn::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.2), transparent);
            transition: left 0.5s;
        }
        
        .service-btn:hover::before {
            left: 100%;
        }
        
        .service-btn.primary {
            background: linear-gradient(135deg, #0066cc 0%, #3d8bff 100%);
            color: white;
            border: none;
            box-shadow: 0 2px 8px rgba(0,102,204,0.2);
        }
        
        .service-btn.primary:hover {
            background: linear-gradient(135deg, #0052a3 0%, #0066cc 100%);
            transform: translateY(-1px);
            box-shadow: 0 4px 12px rgba(0,102,204,0.3);
        }
        
        .service-btn.secondary {
            background: #f8fafc;
            color: #0066cc;
            border: 1px solid #e5e7eb;
        }
        
        .service-btn.secondary:hover {
            background: #0066cc;
            color: white;
            border-color: #0066cc;
        }
        
        /* 产业监测面板 */
        .monitoring-section {
            background: linear-gradient(135deg, #f8fafc 0%, #e2e8f0 50%, #f8fafc 100%);
            margin: 80px -20px;
            padding: 80px 20px;
            position: relative;
        }
        
        .monitoring-section::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 60 60"><defs><pattern id="dots" width="20" height="20" patternUnits="userSpaceOnUse"><circle cx="10" cy="10" r="1" fill="%23cbd5e1" opacity="0.3"/></pattern></defs><rect width="60" height="60" fill="url(%23dots)"/></svg>');
        }
        
        .monitoring-content {
            max-width: 1600px;
            margin: 0 auto;
            position: relative;
            z-index: 1;
            padding: 0 40px;
        }
        
        .monitoring-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 40px;
        }
        
        .monitoring-panel {
            background: white;
            border-radius: 20px;
            padding: 40px;
            box-shadow: 0 10px 40px rgba(0,0,0,0.06);
            border: 1px solid #e5e7eb;
            position: relative;
            overflow: hidden;
        }
        
        .monitoring-panel::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 6px;
            background: linear-gradient(90deg, #0066cc, #3d8bff, #66a3ff);
        }
        
        .panel-title {
            font-size: 22px;
            font-weight: 600;
            margin-bottom: 32px;
            color: #1a1a1a;
            text-align: center;
            position: relative;
        }
        
        .panel-title::after {
            content: '';
            position: absolute;
            bottom: -8px;
            left: 50%;
            transform: translateX(-50%);
            width: 40px;
            height: 2px;
            background: #0066cc;
        }
        
        .data-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 24px;
        }
        
        .data-item {
            text-align: center;
            padding: 24px 16px;
            background: linear-gradient(135deg, #f8fafc 0%, #f1f5f9 100%);
            border-radius: 12px;
            border: 1px solid #e2e8f0;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }
        
        .data-item::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 2px;
            background: linear-gradient(90deg, #0066cc, #3d8bff);
            transform: scaleX(0);
            transition: transform 0.3s ease;
        }
        
        .data-item:hover::before {
            transform: scaleX(1);
        }
        
        .data-item:hover {
            background: white;
            box-shadow: 0 4px 15px rgba(0,102,204,0.1);
            transform: translateY(-2px);
        }
        
        .data-value {
            font-size: 28px;
            font-weight: 700;
            color: #0066cc;
            margin-bottom: 8px;
            font-family: 'SF Mono', 'Monaco', monospace;
        }
        
        .data-label {
            font-size: 13px;
            color: #6b7280;
            font-weight: 500;
            margin-bottom: 8px;
        }
        
        .growth-indicator {
            font-size: 12px;
            color: #10b981;
            font-weight: 600;
            background: #ecfdf5;
            padding: 4px 8px;
            border-radius: 12px;
            display: inline-block;
        }
        
        .growth-indicator.negative {
            color: #ef4444;
            background: #fef2f2;
        }
        
        /* 成功案例区域 */
        .cases-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(360px, 1fr));
            gap: 32px;
        }
        
        .case-card {
            background: white;
            border-radius: 16px;
            padding: 32px;
            box-shadow: 0 4px 20px rgba(0,0,0,0.04);
            border: 1px solid #e5e7eb;
            border-left: 5px solid #0066cc;
            transition: all 0.3s ease;
            position: relative;
        }
        
        .case-card:hover {
            transform: translateY(-4px);
            box-shadow: 0 12px 30px rgba(0,102,204,0.1);
        }
        
        .case-header {
            display: flex;
            align-items: center;
            gap: 12px;
            margin-bottom: 20px;
        }
        
        .case-icon {
            width: 40px;
            height: 40px;
            background: linear-gradient(135deg, #0066cc 0%, #3d8bff 100%);
            border-radius: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 16px;
        }
        
        .case-title {
            font-size: 18px;
            font-weight: 600;
            color: #1a1a1a;
            flex: 1;
        }
        
        .case-tag {
            background: #eff6ff;
            color: #0066cc;
            padding: 4px 10px;
            border-radius: 12px;
            font-size: 11px;
            font-weight: 500;
        }
        
        .case-content {
            color: #4b5563;
            line-height: 1.7;
            font-size: 15px;
            margin-bottom: 20px;
        }
        
        .case-metrics {
            display: flex;
            gap: 20px;
            margin-top: 20px;
            padding-top: 20px;
            border-top: 1px solid #e5e7eb;
        }
        
        .case-metric {
            text-align: center;
            flex: 1;
        }
        
        .metric-value {
            font-size: 20px;
            font-weight: 700;
            color: #0066cc;
            display: block;
        }
        
        .metric-label {
            font-size: 12px;
            color: #6b7280;
            margin-top: 4px;
        }
        
        /* 平台优势 */
        .advantages-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 32px;
        }
        
        .advantage-card {
            text-align: center;
            padding: 40px 24px;
            background: white;
            border-radius: 16px;
            border: 1px solid #e5e7eb;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }
        
        .advantage-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 4px;
            background: linear-gradient(90deg, #0066cc, #3d8bff);
            transform: scaleX(0);
            transition: transform 0.3s ease;
        }
        
        .advantage-card:hover::before {
            transform: scaleX(1);
        }
        
        .advantage-card:hover {
            box-shadow: 0 8px 30px rgba(0,102,204,0.1);
            transform: translateY(-4px);
        }
        
        .advantage-icon {
            width: 80px;
            height: 80px;
            background: linear-gradient(135deg, #eff6ff 0%, #dbeafe 100%);
            border-radius: 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: #0066cc;
            font-size: 32px;
            margin: 0 auto 24px;
            border: 2px solid #bfdbfe;
        }
        
        .advantage-title {
            font-size: 18px;
            font-weight: 600;
            color: #1a1a1a;
            margin-bottom: 16px;
        }
        
        .advantage-description {
            color: #6b7280;
            line-height: 1.6;
            font-size: 14px;
        }
        
        /* 新闻动态区域 */
        .news-section {
            background: #f8fafc;
            margin: 80px -20px;
            padding: 80px 20px;
            position: relative;
        }
        
        .news-content {
            max-width: 1600px;
            margin: 0 auto;
            position: relative;
            z-index: 1;
            padding: 0 40px;
        }
        
        .news-grid {
            display: grid;
            grid-template-columns: 2fr 1fr;
            gap: 40px;
        }
        
        .news-main {
            background: white;
            border-radius: 16px;
            padding: 32px;
            box-shadow: 0 4px 20px rgba(0,0,0,0.04);
            border: 1px solid #e5e7eb;
        }
        
        .news-tabs {
            display: flex;
            gap: 0;
            margin-bottom: 32px;
            border-bottom: 1px solid #e5e7eb;
        }
        
        .news-tab {
            padding: 12px 24px;
            cursor: pointer;
            color: #6b7280;
            font-weight: 500;
            border-bottom: 2px solid transparent;
            transition: all 0.3s ease;
            position: relative;
        }
        
        .news-tab.active {
            color: #0066cc;
            border-bottom-color: #0066cc;
        }
        
        .news-tab:hover {
            color: #0066cc;
        }
        
        .news-list {
            list-style: none;
        }
        
        .news-item {
            display: flex;
            align-items: center;
            padding: 16px 0;
            border-bottom: 1px solid #f3f4f6;
            transition: all 0.3s ease;
        }
        
        .news-item:hover {
            background: #f8fafc;
            margin: 0 -16px;
            padding-left: 16px;
            padding-right: 16px;
            border-radius: 8px;
        }
        
        .news-item:last-child {
            border-bottom: none;
        }
        
        .news-date {
            background: #0066cc;
            color: white;
            padding: 8px 12px;
            border-radius: 8px;
            font-size: 12px;
            font-weight: 600;
            text-align: center;
            min-width: 60px;
            margin-right: 16px;
        }
        
        .news-content-text {
            flex: 1;
        }
        
        .news-title {
            font-size: 15px;
            color: #1a1a1a;
            font-weight: 500;
            margin-bottom: 4px;
            line-height: 1.4;
        }
        
        .news-summary {
            font-size: 13px;
            color: #6b7280;
            line-height: 1.4;
        }
        
        .news-sidebar {
            display: flex;
            flex-direction: column;
            gap: 24px;
        }
        
        .sidebar-card {
            background: white;
            border-radius: 16px;
            padding: 24px;
            box-shadow: 0 4px 20px rgba(0,0,0,0.04);
            border: 1px solid #e5e7eb;
        }
        
        .sidebar-title {
            font-size: 16px;
            font-weight: 600;
            color: #1a1a1a;
            margin-bottom: 20px;
            display: flex;
            align-items: center;
            gap: 8px;
        }
        
        .sidebar-icon {
            width: 20px;
            height: 20px;
            background: #0066cc;
            border-radius: 4px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 10px;
        }
        
        .quick-links {
            list-style: none;
        }
        
        .quick-links li {
            margin-bottom: 12px;
        }
        
        .quick-links a {
            color: #4b5563;
            text-decoration: none;
            font-size: 14px;
            display: flex;
            align-items: center;
            gap: 8px;
            padding: 8px 0;
            transition: color 0.3s ease;
        }
        
        .quick-links a:hover {
            color: #0066cc;
        }
        
        .quick-links a::before {
            content: '▶';
            font-size: 8px;
            color: #0066cc;
        }
        
        /* 底部区域 */
        .footer {
            background: linear-gradient(135deg, #1e293b 0%, #334155 100%);
            color: white;
            padding: 60px 0 30px;
            position: relative;
            overflow: hidden;
        }
        
        .footer::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100"><defs><pattern id="footerPattern" width="40" height="40" patternUnits="userSpaceOnUse"><circle cx="20" cy="20" r="1" fill="white" opacity="0.05"/></pattern></defs><rect width="100" height="100" fill="url(%23footerPattern)"/></svg>');
        }
        
        .footer-content {
            max-width: 1600px;
            margin: 0 auto;
            padding: 0 40px;
            position: relative;
            z-index: 1;
        }
        
        .footer-grid {
            display: grid;
            grid-template-columns: 2fr 1fr 1fr 1fr;
            gap: 50px;
            margin-bottom: 40px;
        }
        
        .footer-brand {
            display: flex;
            flex-direction: column;
        }
        
        .footer-logo {
            display: flex;
            align-items: center;
            gap: 12px;
            margin-bottom: 20px;
        }
        
        .footer-logo-icon {
            width: 40px;
            height: 40px;
            background: linear-gradient(135deg, #0066cc 0%, #3d8bff 100%);
            border-radius: 8px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 16px;
            font-weight: 700;
        }
        
        .footer-brand-name {
            font-size: 18px;
            font-weight: 600;
            color: white;
        }
        
        .footer-description {
            color: #94a3b8;
            line-height: 1.6;
            margin-bottom: 24px;
            font-size: 14px;
        }
        
        .footer-contact {
            display: flex;
            flex-direction: column;
            gap: 12px;
        }
        
        .contact-item {
            display: flex;
            align-items: center;
            gap: 12px;
            color: #cbd5e1;
            font-size: 14px;
        }
        
        .contact-icon {
            width: 16px;
            height: 16px;
            background: #0066cc;
            border-radius: 4px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 8px;
            flex-shrink: 0;
        }
        
        .footer-section h3 {
            font-size: 16px;
            margin-bottom: 20px;
            color: white;
            font-weight: 600;
            position: relative;
        }
        
        .footer-section h3::after {
            content: '';
            position: absolute;
            bottom: -8px;
            left: 0;
            width: 30px;
            height: 2px;
            background: #0066cc;
        }
        
        .footer-section ul {
            list-style: none;
        }
        
        .footer-section li {
            margin-bottom: 12px;
        }
        
        .footer-section a {
            color: #94a3b8;
            text-decoration: none;
            transition: color 0.3s ease;
            font-size: 14px;
            display: flex;
            align-items: center;
            gap: 8px;
        }
        
        .footer-section a:hover {
            color: #3d8bff;
        }
        
        .footer-section a::before {
            content: '•';
            color: #0066cc;
            font-weight: bold;
        }
        
        .footer-bottom {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding-top: 30px;
            border-top: 1px solid #334155;
        }
        
        .footer-copyright {
            color: #94a3b8;
            font-size: 13px;
        }
        
        .footer-links {
            display: flex;
            gap: 24px;
        }
        
        .footer-links a {
            color: #94a3b8;
            text-decoration: none;
            font-size: 13px;
            transition: color 0.3s ease;
        }
        
        .footer-links a:hover {
            color: #3d8bff;
        }
        
        /* 响应式设计 */
        @media (max-width: 1400px) {
            .header-content,
            .hero-content,
            .main-content,
            .monitoring-content,
            .news-content,
            .footer-content {
                max-width: 1200px;
                padding-left: 20px;
                padding-right: 20px;
            }
            
            .hero-content {
                grid-template-columns: 1fr 400px;
                gap: 60px;
            }
            
            .logo-section {
                max-width: 300px;
            }
            
            .main-nav {
                max-width: 420px;
                margin: 0 2px;
                gap: 1px;
            }
            
            .nav-item {
                padding: 5px 3px;
                font-size: 11px;
                min-width: 45px;
            }
            
            .user-section {
                max-width: 210px;
                gap: 6px;
            }
        }
        
        @media (max-width: 1200px) {
            .platform-name {
                font-size: 20px;
            }
            
            .platform-name .sub {
                font-size: 13px;
            }
            
            .logo-section {
                max-width: 280px;
            }
            
            .main-nav {
                max-width: 360px;
                margin: 0 1px;
                gap: 0px;
            }
            
            .nav-item {
                padding: 4px 2px;
                font-size: 10px;
                min-width: 40px;
            }
            
            .user-section {
                max-width: 180px;
                gap: 4px;
            }
            
            .login-btn {
                min-width: 50px;
                padding: 6px 10px;
                font-size: 10px;
            }
        }
        
        @media (max-width: 1024px) {
            .header-content {
                flex-direction: column;
                gap: 8px;
                height: auto;
                padding: 8px 10px;
            }
            
            .logo-section {
                max-width: none;
            }
            
            .main-nav {
                max-width: 320px;
                margin: 0;
                gap: 0px;
            }
            
            .nav-item {
                padding: 4px 2px;
                font-size: 9px;
                min-width: 35px;
            }
            
            .user-section {
                max-width: none;
                justify-content: center;
            }
            
            .hero-content {
                grid-template-columns: 1fr;
                gap: 40px;
                text-align: center;
            }
            
            .monitoring-grid {
                grid-template-columns: 1fr;
            }
            
            .news-grid {
                grid-template-columns: 1fr;
            }
            
            .footer-grid {
                grid-template-columns: 1fr 1fr;
                gap: 30px;
            }
        }
        
        @media (max-width: 768px) {
            .header-content {
                flex-direction: row;
                height: 70px;
                padding: 10px 15px;
                gap: 10px;
                position: relative;
            }
            
            .logo-section {
                justify-content: flex-start;
                flex: 1;
            }
            
            .platform-name {
                font-size: 16px;
            }
            
            .platform-name .sub {
                font-size: 11px;
            }
            
            .main-nav {
                display: none;
            }
            
            .mobile-menu-toggle {
                display: flex;
            }
            
            .user-section {
                display: none;
            }
            
            .hero-content {
                padding: 40px 15px;
                grid-template-columns: 1fr;
                gap: 30px;
                text-align: center;
            }
            
            .hero-title {
                font-size: 24px;
                line-height: 1.2;
            }
            
            .hero-subtitle {
                font-size: 14px;
            }
            
            .stats-dashboard {
                padding: 20px;
            }
            
            .stats-grid {
                grid-template-columns: 1fr 1fr;
                gap: 15px;
            }
            
            .stat-number {
                font-size: 20px;
            }
            
            .stat-label {
                font-size: 11px;
            }
            
            .hero-cta {
                flex-direction: column;
                align-items: center;
                gap: 12px;
            }
            
            .cta-btn {
                padding: 12px 24px;
                font-size: 14px;
                width: 100%;
                max-width: 280px;
            }
            
            .services-grid {
                grid-template-columns: 1fr;
                gap: 20px;
            }
            
            .service-card {
                padding: 24px;
            }
            
            .service-icon {
                width: 48px;
                height: 48px;
                font-size: 20px;
            }
            
            .service-title {
                font-size: 18px;
            }
            
            .service-description {
                font-size: 14px;
            }
            
            .service-buttons {
                flex-direction: column;
                gap: 8px;
            }
            
            .monitoring-grid {
                grid-template-columns: 1fr;
                gap: 20px;
            }
            
            .monitoring-panel {
                padding: 20px;
            }
            
            .data-grid {
                grid-template-columns: 1fr 1fr;
                gap: 15px;
            }
            
            .data-item {
                padding: 15px 8px;
            }
            
            .data-value {
                font-size: 20px;
            }
            
            .data-label {
                font-size: 11px;
            }
            
            .cases-grid {
                grid-template-columns: 1fr;
                gap: 20px;
            }
            
            .case-card {
                padding: 20px;
            }
            
            .case-metrics {
                flex-direction: column;
                gap: 10px;
            }
            
            .case-metric {
                text-align: left;
            }
            
            .metric-value {
                font-size: 16px;
            }
            
            .advantages-grid {
                grid-template-columns: 1fr;
                gap: 20px;
            }
            
            .advantage-card {
                padding: 24px 16px;
            }
            
            .advantage-icon {
                width: 60px;
                height: 60px;
                font-size: 24px;
            }
            
            .news-grid {
                grid-template-columns: 1fr;
                gap: 20px;
            }
            
            .news-main {
                padding: 20px;
            }
            
            .news-tabs {
                flex-wrap: wrap;
                gap: 5px;
            }
            
            .news-tab {
                padding: 8px 12px;
                font-size: 13px;
            }
            
            .news-item {
                flex-direction: column;
                align-items: flex-start;
                gap: 8px;
            }
            
            .news-date {
                align-self: flex-start;
                min-width: 50px;
                margin-right: 0;
            }
            
            .sidebar-card {
                padding: 16px;
            }
            
            .footer-grid {
                grid-template-columns: 1fr;
                gap: 25px;
            }
            
            .footer-bottom {
                flex-direction: column;
                gap: 12px;
                text-align: center;
            }
            
            .footer-links {
                flex-wrap: wrap;
                justify-content: center;
                gap: 12px;
            }
        }
        
        @media (max-width: 480px) {
            .header-content {
                padding: 8px 12px;
                height: 60px;
            }
            
            .logo {
                width: 45px;
                height: 45px;
                font-size: 18px;
            }
            
            .platform-name {
                font-size: 14px;
            }
            
            .platform-name .sub {
                font-size: 10px;
            }
            
            .mobile-menu-toggle {
                padding: 6px;
            }
            
            .mobile-menu-toggle span {
                width: 16px;
                height: 1.5px;
            }
            
            .mobile-nav-item {
                padding: 10px 15px;
                font-size: 13px;
            }
            
            .hero-content {
                padding: 30px 12px;
            }
            
            .hero-title {
                font-size: 20px;
            }
            
            .hero-subtitle {
                font-size: 13px;
            }
            
            .stats-dashboard {
                padding: 15px;
            }
            
            .stats-grid {
                grid-template-columns: 1fr;
                gap: 12px;
            }
            
            .stat-item {
                padding: 12px;
            }
            
            .stat-number {
                font-size: 18px;
            }
            
            .cta-btn {
                padding: 10px 20px;
                font-size: 13px;
            }
            
            .main-content {
                padding: 40px 12px;
            }
            
            .section-title {
                font-size: 24px;
            }
            
            .service-card {
                padding: 20px;
            }
            
            .service-icon {
                width: 40px;
                height: 40px;
                font-size: 16px;
            }
            
            .service-title {
                font-size: 16px;
            }
            
            .monitoring-section {
                padding: 40px 12px;
            }
            
            .monitoring-panel {
                padding: 16px;
            }
            
            .data-grid {
                grid-template-columns: 1fr;
                gap: 12px;
            }
            
            .data-item {
                padding: 12px;
            }
            
            .case-card {
                padding: 16px;
            }
            
            .advantage-card {
                padding: 20px 12px;
            }
            
            .advantage-icon {
                width: 50px;
                height: 50px;
                font-size: 20px;
            }
            
            .news-section {
                padding: 40px 12px;
            }
            
            .news-main {
                padding: 16px;
            }
            
            .sidebar-card {
                padding: 12px;
            }
            
            .footer {
                padding: 30px 0 20px;
            }
            
            .footer-content {
                padding: 0 12px;
            }
        }
        
        /* 滚动动画 */
        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(40px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }
        
        @keyframes slideInLeft {
            from {
                opacity: 0;
                transform: translateX(-40px);
            }
            to {
                opacity: 1;
                transform: translateX(0);
            }
        }
        
        @keyframes slideInRight {
            from {
                opacity: 0;
                transform: translateX(40px);
            }
            to {
                opacity: 1;
                transform: translateX(0);
            }
        }
        
        .service-card:nth-child(odd) {
            animation: slideInLeft 0.8s ease-out;
        }
        
        .service-card:nth-child(even) {
            animation: slideInRight 0.8s ease-out;
        }
        
        .monitoring-panel,
        .case-card,
        .advantage-card {
            animation: fadeInUp 0.8s ease-out;
        }
        
        /* 数字滚动效果 */
        @keyframes countUp {
            from {
                opacity: 0;
                transform: scale(0.5) rotateY(180deg);
            }
            to {
                opacity: 1;
                transform: scale(1) rotateY(0deg);
            }
        }
        
        .stat-number,
        .data-value,
        .metric-value {
            animation: countUp 1s ease-out 0.5s both;
        }
        
        /* 加载动画 */
        .loading-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: white;
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 9999;
            transition: opacity 0.5s ease;
        }
        
        .loading-spinner {
            width: 50px;
            height: 50px;
            border: 4px solid #e5e7eb;
            border-top: 4px solid #0066cc;
            border-radius: 50%;
            animation: spin 1s linear infinite;
        }
        
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        
        /* 滚动条样式 */
        ::-webkit-scrollbar {
            width: 8px;
        }
        
        ::-webkit-scrollbar-track {
            background: #f1f5f9;
        }
        
        ::-webkit-scrollbar-thumb {
            background: #cbd5e1;
            border-radius: 4px;
        }
        
        ::-webkit-scrollbar-thumb:hover {
            background: #94a3b8;
        }
    </style>
</head>
<body>
    <!-- 加载动画 -->
    <div class="loading-overlay" id="loadingOverlay">
        <div class="loading-spinner"></div>
    </div>

    <!-- 顶部公告栏 -->
    <div class="top-notice">
        <div class="notice-content">
            🎉 欢迎使用产业大脑区域经济综合服务平台 | 全新升级，助力企业数字化转型 | 24小时在线服务
        </div>
    </div>

    <!-- 顶部导航 -->
    <header class="header">
        <div class="header-content">
            <div class="logo-section">
                <div class="logo">产</div>
                <div class="platform-name">
                    产业大脑区域经济综合服务平台
                    <span class="sub">Industrial Brain Regional Economic Service Platform</span>
                </div>
            </div>
            
            <nav class="main-nav">
                <div class="nav-item active">政策服务</div>
                <div class="nav-item">金融服务</div>
                <div class="nav-item">信用服务</div>
                <div class="nav-item">数据服务</div>
                <div class="nav-item">人才服务</div>
                <div class="nav-item">会展服务</div>
                <div class="nav-item">供需集市</div>
                <div class="nav-item">产业园区</div>
            </nav>
            
            <div class="user-section">
                <button class="login-btn">企业登录</button>
                <button class="login-btn">政府端</button>
                <button class="login-btn primary">服务商登录</button>
            </div>
            
            <!-- 移动端菜单按钮 -->
            <button class="mobile-menu-toggle" id="mobileMenuToggle" type="button" aria-label="打开菜单">
                <span></span>
                <span></span>
                <span></span>
            </button>
        </div>
        
        <!-- 移动端导航菜单 -->
        <nav class="mobile-nav" id="mobileNav">
            <div class="mobile-nav-item active" data-nav="政策服务">政策服务</div>
            <div class="mobile-nav-item" data-nav="金融服务">金融服务</div>
            <div class="mobile-nav-item" data-nav="信用服务">信用服务</div>
            <div class="mobile-nav-item" data-nav="数据服务">数据服务</div>
            <div class="mobile-nav-item" data-nav="人才服务">人才服务</div>
            <div class="mobile-nav-item" data-nav="会展服务">会展服务</div>
            <div class="mobile-nav-item" data-nav="供需集市">供需集市</div>
            <div class="mobile-nav-item" data-nav="产业园区">产业园区</div>
            <div class="mobile-nav-divider">
                <div class="mobile-nav-item" data-nav="企业登录">企业登录</div>
                <div class="mobile-nav-item" data-nav="政府端">政府端登录</div>
                <div class="mobile-nav-item" data-nav="服务商登录" style="color: #0066cc; font-weight: 600;">服务商登录</div>
            </div>
        </nav>
    </header>

    <!-- 核心价值展示区 -->
    <section class="hero-section">
        <div class="hero-content">
            <div class="hero-text">
                <h1 class="hero-title">构建城市"产业大脑"<br>赋能新质生产力发展</h1>
                <p class="hero-subtitle">运用大数据、云计算、人工智能技术，打通产业链、空间链、供应链、创新链，促进四链融合创新应用，为区域经济高质量发展提供智能化综合服务。</p>
                
                <div class="hero-features">
                    <div class="feature-item">
                        <div class="feature-icon">✓</div>
                        <span>政府权威数据支撑</span>
                    </div>
                    <div class="feature-item">
                        <div class="feature-icon">✓</div>
                        <span>AI智能精准匹配</span>
                    </div>
                    <div class="feature-item">
                        <div class="feature-icon">✓</div>
                        <span>一站式综合服务</span>
                    </div>
                    <div class="feature-item">
                        <div class="feature-icon">✓</div>
                        <span>全流程数字化管理</span>
                    </div>
                </div>
                
                <div class="hero-cta">
                    <a href="#" class="cta-btn primary">立即体验</a>
                    <a href="#" class="cta-btn secondary">了解更多</a>
                </div>
            </div>
            
            <div class="hero-visual">
                <div class="stats-dashboard">
                    <h3 class="dashboard-title">实时服务数据</h3>
                    <div class="stats-grid">
                        <div class="stat-item">
                            <span class="stat-number">8,765</span>
                            <div class="stat-label">服务企业数量</div>
                        </div>
                        <div class="stat-item">
                            <span class="stat-number">236.8</span>
                            <div class="stat-label">交易金额（亿元）</div>
                        </div>
                        <div class="stat-item">
                            <span class="stat-number">93.2%</span>
                            <div class="stat-label">政策匹配成功率</div>
                        </div>
                        <div class="stat-item">
                            <span class="stat-number">15.6</span>
                            <div class="stat-label">活跃用户（万）</div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- 主要内容区域 -->
    <main class="main-content">
        <!-- 综合服务体系 -->
        <section class="section">
            <div class="section-header">
                <h2 class="section-title">综合服务体系</h2>
                <p class="section-subtitle">为企业提供覆盖全生命周期的一站式数字化服务，助力产业转型升级</p>
            </div>
            
            <div class="services-grid">
                <!-- 政策服务 -->
                <div class="service-card">
                    <div class="service-header">
                        <div class="service-icon">📋</div>
                        <div>
                            <h3 class="service-title">政策服务</h3>
                            <span class="service-tag">智能推荐</span>
                        </div>
                    </div>
                    <p class="service-description">建设全量政策数据库，运用AI技术实现政策智能匹配和精准推送，简化申报流程，提高政策落地效率。</p>
                    <ul class="service-features">
                        <li>惠企政策智能推送，精准匹配企业需求</li>
                        <li>一键申报服务，简化办事流程</li>
                        <li>专业政策解读，政策红利最大化</li>
                        <li>申报进度实时跟踪，透明化管理</li>
                    </ul>
                    <div class="service-buttons">
                        <a href="#" class="service-btn primary">查看政策</a>
                        <a href="#" class="service-btn secondary">立即申报</a>
                    </div>
                </div>

                <!-- 金融服务 -->
                <div class="service-card">
                    <div class="service-header">
                        <div class="service-icon">💰</div>
                        <div>
                            <h3 class="service-title">金融服务</h3>
                            <span class="service-tag">普惠金融</span>
                        </div>
                    </div>
                    <p class="service-description">汇聚银行、保险、投资机构等金融资源，为企业提供多元化金融产品和个性化融资解决方案。</p>
                    <ul class="service-features">
                        <li>200+金融产品聚合展示</li>
                        <li>智能推荐匹配，提升融资成功率</li>
                        <li>在线申请服务，7×24小时响应</li>
                        <li>专业风险评估，降低融资成本</li>
                    </ul>
                    <div class="service-buttons">
                        <a href="#" class="service-btn primary">查看产品</a>
                        <a href="#" class="service-btn secondary">申请贷款</a>
                    </div>
                </div>

                <!-- 信用服务 -->
                <div class="service-card">
                    <div class="service-header">
                        <div class="service-icon">🎖️</div>
                        <div>
                            <h3 class="service-title">信用服务</h3>
                            <span class="service-tag">权威认证</span>
                        </div>
                    </div>
                    <p class="service-description">构建企业信用大数据平台，提供征信管理、信用评估、诚信认证等全方位信用服务生态。</p>
                    <ul class="service-features">
                        <li>360°企业信用画像，多维度评估</li>
                        <li>权威信用评级认证，提升企业形象</li>
                        <li>信用+场景应用，享受绿色通道</li>
                        <li>信用修复指导，助力企业发展</li>
                    </ul>
                    <div class="service-buttons">
                        <a href="#" class="service-btn primary">信用查询</a>
                        <a href="#" class="service-btn secondary">申请认证</a>
                    </div>
                </div>

                <!-- 数据服务 -->
                <div class="service-card">
                    <div class="service-header">
                        <div class="service-icon">📊</div>
                        <div>
                            <h3 class="service-title">数据服务</h3>
                            <span class="service-tag">智能分析</span>
                        </div>
                    </div>
                    <p class="service-description">基于大数据技术构建产业监测体系，提供企业画像、行业分析、趋势预测等数据智能服务。</p>
                    <ul class="service-features">
                        <li>实时产业运行监测，把握发展脉搏</li>
                        <li>企业对标分析，发现竞争优势</li>
                        <li>定制化行业报告，辅助决策制定</li>
                        <li>预警预测服务，防范经营风险</li>
                    </ul>
                    <div class="service-buttons">
                        <a href="#" class="service-btn primary">查看数据</a>
                        <a href="#" class="service-btn secondary">定制报告</a>
                    </div>
                </div>

                <!-- 人才服务 -->
                <div class="service-card">
                    <div class="service-header">
                        <div class="service-icon">👥</div>
                        <div>
                            <h3 class="service-title">人才服务</h3>
                            <span class="service-tag">智慧招聘</span>
                        </div>
                    </div>
                    <p class="service-description">打造人才供需对接平台，提供招聘服务、技能培训、灵活用工等全链条人才解决方案。</p>
                    <ul class="service-features">
                        <li>精准人才供需匹配，提升招聘效率</li>
                        <li>专业技能培训体系，提升人才质量</li>
                        <li>灵活用工服务，降低用工成本</li>
                        <li>人才评估测评，科学选人用人</li>
                    </ul>
                    <div class="service-buttons">
                        <a href="#" class="service-btn primary">发布需求</a>
                        <a href="#" class="service-btn secondary">查找人才</a>
                    </div>
                </div>

                <!-- 会展服务 -->
                <div class="service-card">
                    <div class="service-header">
                        <div class="service-icon">🏢</div>
                        <div>
                            <h3 class="service-title">会展服务</h3>
                            <span class="service-tag">数字展会</span>
                        </div>
                    </div>
                    <p class="service-description">整合会展资源，提供线上线下融合的展会服务，促进产业交流合作和商机对接。</p>
                    <ul class="service-features">
                        <li>权威展会信息发布，一站式获取资讯</li>
                        <li>智能参展商招募，精准匹配目标客户</li>
                        <li>全程现场服务支持，保障展会效果</li>
                        <li>数字化展示平台，拓展展会边界</li>
                    </ul>
                    <div class="service-buttons">
                        <a href="#" class="service-btn primary">查看展会</a>
                        <a href="#" class="service-btn secondary">申请参展</a>
                    </div>
                </div>
            </div>
        </section>

        <!-- 产业监测大屏 -->
        <section class="monitoring-section">
            <div class="monitoring-content">
                <div class="section-header">
                    <h2 class="section-title">产业运行监测</h2>
                    <p class="section-subtitle">实时掌握区域经济运行态势，为政府决策和企业发展提供数据支撑</p>
                </div>
                
                <div class="monitoring-grid">
                    <div class="monitoring-panel">
                        <h3 class="panel-title">区域经济指标</h3>
                        <div class="data-grid">
                            <div class="data-item">
                                <div class="data-value">156.8</div>
                                <div class="data-label">累计订单金额（亿元）</div>
                                <div class="growth-indicator">↑ 环比增长 18.7%</div>
                            </div>
                            <div class="data-item">
                                <div class="data-value">13.2%</div>
                                <div class="data-label">平均利润率</div>
                                <div class="growth-indicator">↑ 提升 2.1%</div>
                            </div>
                            <div class="data-item">
                                <div class="data-value">25.6</div>
                                <div class="data-label">在岗职工数（万人）</div>
                                <div class="growth-indicator">↑ 同比增长 4.5%</div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- 成功案例展示 -->
        <section class="section">
            <div class="section-header">
                <h2 class="section-title">成功案例展示</h2>
                <p class="section-subtitle">真实案例见证平台价值，助力更多企业实现发展目标</p>
            </div>
            
            <div class="cases-grid">
                <div class="case-card">
                    <div class="case-header">
                        <div class="case-icon">📋</div>
                        <h3 class="case-title">政策服务成功案例</h3>
                        <span class="case-tag">智能匹配</span>
                    </div>
                    <p class="case-content">某制造业企业通过平台智能政策匹配系统，成功申请到技术改造补贴500万元、研发费用加计扣除300万元，有效降低了企业运营成本15%，提升了产品市场竞争力。</p>
                    <div class="case-metrics">
                        <div class="case-metric">
                            <span class="metric-value">800万</span>
                            <div class="metric-label">获得补贴</div>
                        </div>
                        <div class="case-metric">
                            <span class="metric-value">15%</span>
                            <div class="metric-label">成本降低</div>
                        </div>
                        <div class="case-metric">
                            <span class="metric-value">7天</span>
                            <div class="metric-label">办理时长</div>
                        </div>
                    </div>
                </div>
                
                <div class="case-card">
                    <div class="case-header">
                        <div class="case-icon">💰</div>
                        <h3 class="case-title">金融服务成功案例</h3>
                        <span class="case-tag">快速放款</span>
                    </div>
                    <p class="case-content">某科技企业通过平台金融服务，获得银行授信2000万元，解决了扩产资金需求。年产值提升40%，新增就业岗位120个，实现了企业快速发展。</p>
                    <div class="case-metrics">
                        <div class="case-metric">
                            <span class="metric-value">2000万</span>
                            <div class="metric-label">授信额度</div>
                        </div>
                        <div class="case-metric">
                            <span class="metric-value">40%</span>
                            <div class="metric-label">产值提升</div>
                        </div>
                        <div class="case-metric">
                            <span class="metric-value">3天</span>
                            <div class="metric-label">放款时间</div>
                        </div>
                    </div>
                </div>
                
                <div class="case-card">
                    <div class="case-header">
                        <div class="case-icon">🔗</div>
                        <h3 class="case-title">产业协同成功案例</h3>
                        <span class="case-tag">供需对接</span>
                    </div>
                    <p class="case-content">通过平台供需匹配功能，某汽车零部件企业与3家上游供应商达成合作协议，建立稳定供应链体系，降低采购成本12%，提升供应链效率25%。</p>
                    <div class="case-metrics">
                        <div class="case-metric">
                            <span class="metric-value">3家</span>
                            <div class="metric-label">合作伙伴</div>
                        </div>
                        <div class="case-metric">
                            <span class="metric-value">12%</span>
                            <div class="metric-label">成本降低</div>
                        </div>
                        <div class="case-metric">
                            <span class="metric-value">25%</span>
                            <div class="metric-label">效率提升</div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- 平台优势 -->
        <section class="section">
            <div class="section-header">
                <h2 class="section-title">平台核心优势</h2>
                <p class="section-subtitle">依托政府权威数据和先进技术，为区域经济发展提供强有力支撑</p>
            </div>
            
            <div class="advantages-grid">
                <div class="advantage-card">
                    <div class="advantage-icon">📊</div>
                    <h3 class="advantage-title">数据驱动决策</h3>
                    <p class="advantage-description">依托政府权威数据和大数据分析技术，为企业和政府提供精准的数据洞察和决策支持，助力科学决策。</p>
                </div>
                
                <div class="advantage-card">
                    <div class="advantage-icon">🔗</div>
                    <h3 class="advantage-title">四链深度融合</h3>
                    <p class="advantage-description">打通产业链、空间链、供应链、创新链，实现四链深度融合，构建完整的产业生态服务体系。</p>
                </div>
                
                <div class="advantage-card">
                    <div class="advantage-icon">🏛️</div>
                    <h3 class="advantage-title">政府权威背书</h3>
                    <p class="advantage-description">政府官方平台，数据来源权威可信，服务质量有保障，为企业发展提供可靠的政策和资源支持。</p>
                </div>
                
                <div class="advantage-card">
                    <div class="advantage-icon">🎯</div>
                    <h3 class="advantage-title">一站式服务</h3>
                    <p class="advantage-description">涵盖企业全生命周期服务需求，从注册到发展壮大，提供全方位、一站式的综合服务解决方案。</p>
                </div>
            </div>
        </section>
    </main>

    <!-- 新闻动态区域 -->
    <section class="news-section">
        <div class="news-content">
            <div class="section-header">
                <h2 class="section-title">新闻动态</h2>
                <p class="section-subtitle">及时了解最新政策资讯和平台动态</p>
            </div>
            
            <div class="news-grid">
                <div class="news-main">
                    <div class="news-tabs">
                        <div class="news-tab active">政策发布</div>
                        <div class="news-tab">平台动态</div>
                        <div class="news-tab">行业资讯</div>
                        <div class="news-tab">活动公告</div>
                    </div>
                    
                    <ul class="news-list">
                        <li class="news-item">
                            <div class="news-date">12-15</div>
                            <div class="news-content-text">
                                <div class="news-title">《关于支持制造业高质量发展的若干政策措施》正式发布</div>
                                <div class="news-summary">新政策将在技术改造、数字化转型、绿色发展等方面给予企业更大支持...</div>
                            </div>
                        </li>
                        <li class="news-item">
                            <div class="news-date">12-12</div>
                            <div class="news-content-text">
                                <div class="news-title">产业大脑平台金融服务模块全新升级，新增投资对接功能</div>
                                <div class="news-summary">平台新增股权投资、债权融资等多种投融资对接服务，为企业提供更丰富的资金来源...</div>
                            </div>
                        </li>
                        <li class="news-item">
                            <div class="news-date">12-10</div>
                            <div class="news-content-text">
                                <div class="news-title">2024年度中小企业数字化转型专项扶持计划启动申报</div>
                                <div class="news-summary">单个企业最高可获得100万元资金支持，重点支持智能制造、工业互联网等项目...</div>
                            </div>
                        </li>
                        <li class="news-item">
                            <div class="news-date">12-08</div>
                            <div class="news-content-text">
                                <div class="news-title">区域产业合作交流会成功举办，签约项目总投资超50亿元</div>
                                <div class="news-summary">本次交流会汇聚了200多家企业，促成了多项产业链上下游合作协议...</div>
                            </div>
                        </li>
                        <li class="news-item">
                            <div class="news-date">12-05</div>
                            <div class="news-content-text">
                                <div class="news-title">平台人才服务模块上线"技能培训在线课堂"功能</div>
                                <div class="news-summary">提供涵盖数字技能、管理技能、专业技能等多个领域的在线培训课程...</div>
                            </div>
                        </li>
                    </ul>
                </div>
                
                <div class="news-sidebar">
                    <div class="sidebar-card">
                        <h3 class="sidebar-title">
                            <div class="sidebar-icon">🔗</div>
                            快速链接
                        </h3>
                        <ul class="quick-links">
                            <li><a href="#">政策申报指南</a></li>
                            <li><a href="#">企业注册入驻</a></li>
                            <li><a href="#">金融产品查询</a></li>
                            <li><a href="#">信用评级申请</a></li>
                            <li><a href="#">数据服务定制</a></li>
                            <li><a href="#">人才招聘发布</a></li>
                            <li><a href="#">展会活动报名</a></li>
                        </ul>
                    </div>
                    
                    <div class="sidebar-card">
                        <h3 class="sidebar-title">
                            <div class="sidebar-icon">📞</div>
                            联系我们
                        </h3>
                        <div class="contact-info">
                            <div class="contact-item">
                                <div class="contact-icon">📞</div>
                                <span>400-888-6666</span>
                            </div>
                            <div class="contact-item">
                                <div class="contact-icon">✉️</div>
                                <span>service@industry-brain.gov.cn</span>
                            </div>
                            <div class="contact-item">
                                <div class="contact-icon">🕒</div>
                                <span>工作时间：9:00-18:00</span>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- 底部区域 -->
    <footer class="footer">
        <div class="footer-content">
            <div class="footer-grid">
                <div class="footer-brand">
                    <div class="footer-logo">
                        <div class="footer-logo-icon">产</div>
                        <div class="footer-brand-name">产业大脑区域经济综合服务平台</div>
                    </div>
                    <p class="footer-description">
                        依托大数据、云计算、人工智能等先进技术，构建区域产业发展智能化服务生态，助力新质生产力发展，推动区域经济高质量发展。
                    </p>
                    <div class="footer-contact">
                        <div class="contact-item">
                            <div class="contact-icon">📍</div>
                            <span>北京市海淀区中关村科技园区</span>
                        </div>
                        <div class="contact-item">
                            <div class="contact-icon">📞</div>
                            <span>客服热线：400-888-6666</span>
                        </div>
                        <div class="contact-item">
                            <div class="contact-icon">✉️</div>
                            <span>service@industry-brain.gov.cn</span>
                        </div>
                    </div>
                </div>
                
                <div class="footer-section">
                    <h3>平台服务</h3>
                    <ul>
                        <li><a href="#">政策服务</a></li>
                        <li><a href="#">金融服务</a></li>
                        <li><a href="#">信用服务</a></li>
                        <li><a href="#">数据服务</a></li>
                        <li><a href="#">人才服务</a></li>
                        <li><a href="#">会展服务</a></li>
                    </ul>
                </div>
                
                <div class="footer-section">
                    <h3>帮助支持</h3>
                    <ul>
                        <li><a href="#">使用指南</a></li>
                        <li><a href="#">常见问题</a></li>
                        <li><a href="#">操作手册</a></li>
                        <li><a href="#">视频教程</a></li>
                        <li><a href="#">技术支持</a></li>
                        <li><a href="#">意见反馈</a></li>
                    </ul>
                </div>
                
                <div class="footer-section">
                    <h3>关于我们</h3>
                    <ul>
                        <li><a href="#">平台介绍</a></li>
                        <li><a href="#">发展历程</a></li>
                        <li><a href="#">组织架构</a></li>
                        <li><a href="#">合作伙伴</a></li>
                        <li><a href="#">招商合作</a></li>
                        <li><a href="#">联系我们</a></li>
                    </ul>
                </div>
            </div>
            
            <div class="footer-bottom">
                <div class="footer-copyright">
                    © 2024 产业大脑区域经济综合服务平台 版权所有 | 京ICP备12345678号 | 京公网安备11010802012345号
                </div>
                <div class="footer-links">
                    <a href="#">隐私政策</a>
                    <a href="#">服务条款</a>
                    <a href="#">免责声明</a>
                    <a href="#">网站地图</a>
                </div>
            </div>
        </div>
    </footer>

    <script>
        // 页面加载完成后隐藏加载动画
        window.addEventListener('load', function() {
            setTimeout(function() {
                const loadingOverlay = document.getElementById('loadingOverlay');
                loadingOverlay.style.opacity = '0';
                setTimeout(function() {
                    loadingOverlay.style.display = 'none';
                }, 500);
            }, 1000);
        });

        // 统一跳转函数
        function redirectToSurvey() {
            window.open('https://www.wjx.cn/vm/wIIHcFu.aspx#', '_blank');
        }

        // 移动端菜单切换 - 增强版本
        function initMobileMenu() {
            const mobileMenuToggle = document.getElementById('mobileMenuToggle');
            const mobileNav = document.getElementById('mobileNav');

            if (!mobileMenuToggle || !mobileNav) {
                return;
            }

            // 菜单切换函数
            function toggleMenu(e) {
                e.preventDefault();
                e.stopPropagation();
                
                const isActive = mobileMenuToggle.classList.contains('active');
                
                if (isActive) {
                    mobileMenuToggle.classList.remove('active');
                    mobileNav.classList.remove('active');
                    mobileMenuToggle.setAttribute('aria-label', '打开菜单');
                } else {
                    mobileMenuToggle.classList.add('active');
                    mobileNav.classList.add('active');
                    mobileMenuToggle.setAttribute('aria-label', '关闭菜单');
                }
            }

            // 绑定多种事件确保兼容性
            mobileMenuToggle.addEventListener('click', toggleMenu);
            mobileMenuToggle.addEventListener('touchstart', function(e) {
                e.preventDefault();
                toggleMenu(e);
            });

            // 点击菜单项时的处理
            document.querySelectorAll('.mobile-nav-item').forEach(item => {
                item.addEventListener('click', function(e) {
                    e.preventDefault();
                    
                    const navText = this.getAttribute('data-nav') || this.textContent.trim();
                    
                    // 如果是登录相关项目，直接跳转
                    if (navText.includes('登录')) {
                        redirectToSurvey();
                        return;
                    }
                    
                    // 移除所有激活状态
                    document.querySelectorAll('.mobile-nav-item').forEach(nav => {
                        if (!nav.textContent.includes('登录')) {
                            nav.classList.remove('active');
                        }
                    });
                    document.querySelectorAll('.nav-item').forEach(nav => nav.classList.remove('active'));
                    
                    // 添加当前激活状态
                    this.classList.add('active');
                    
                    // 同步桌面端导航状态
                    document.querySelectorAll('.nav-item').forEach(nav => {
                        if (nav.textContent.trim() === navText) {
                            nav.classList.add('active');
                        }
                    });
                    
                    // 关闭移动端菜单
                    mobileMenuToggle.classList.remove('active');
                    mobileNav.classList.remove('active');
                    mobileMenuToggle.setAttribute('aria-label', '打开菜单');
                    
                    // 跳转到问卷
                    redirectToSurvey();
                });
            });

            // 点击页面其他地方关闭菜单
            document.addEventListener('click', function(e) {
                if (!mobileMenuToggle.contains(e.target) && !mobileNav.contains(e.target)) {
                    mobileMenuToggle.classList.remove('active');
                    mobileNav.classList.remove('active');
                    mobileMenuToggle.setAttribute('aria-label', '打开菜单');
                }
            });

            // 阻止菜单内部点击冒泡
            mobileNav.addEventListener('click', function(e) {
                e.stopPropagation();
            });
        }

        // 初始化所有按钮点击事件
        function initAllButtons() {
            // 登录按钮
            document.querySelectorAll('.login-btn').forEach(btn => {
                btn.addEventListener('click', function(e) {
                    e.preventDefault();
                    redirectToSurvey();
                });
            });

            // Hero区域的CTA按钮
            document.querySelectorAll('.cta-btn').forEach(btn => {
                btn.addEventListener('click', function(e) {
                    e.preventDefault();
                    redirectToSurvey();
                });
            });

            // 快速入口按钮
            document.querySelectorAll('.action-btn').forEach(btn => {
                btn.addEventListener('click', function(e) {
                    e.preventDefault();
                    redirectToSurvey();
                });
            });

            // 服务卡片按钮
            document.querySelectorAll('.service-btn').forEach(btn => {
                btn.addEventListener('click', function(e) {
                    e.preventDefault();
                    redirectToSurvey();
                });
            });

            // 新闻标签切换
            document.querySelectorAll('.news-tab').forEach(tab => {
                tab.addEventListener('click', function(e) {
                    e.preventDefault();
                    
                    // 移除所有激活状态
                    document.querySelectorAll('.news-tab').forEach(t => t.classList.remove('active'));
                    // 添加当前激活状态
                    this.classList.add('active');
                    
                    // 跳转到问卷
                    redirectToSurvey();
                });
            });

            // 新闻项目点击
            document.querySelectorAll('.news-item').forEach(item => {
                item.addEventListener('click', function(e) {
                    e.preventDefault();
                    redirectToSurvey();
                });
            });

            // 快速链接
            document.querySelectorAll('.quick-links a').forEach(link => {
                link.addEventListener('click', function(e) {
                    e.preventDefault();
                    redirectToSurvey();
                });
            });

            // 底部链接
            document.querySelectorAll('.footer-section a').forEach(link => {
                link.addEventListener('click', function(e) {
                    e.preventDefault();
                    redirectToSurvey();
                });
            });

            // 底部版权区域链接
            document.querySelectorAll('.footer-links a').forEach(link => {
                link.addEventListener('click', function(e) {
                    e.preventDefault();
                    redirectToSurvey();
                });
            });

            // 统计数据卡片点击
            document.querySelectorAll('.stat-item').forEach(item => {
                item.addEventListener('click', function(e) {
                    e.preventDefault();
                    redirectToSurvey();
                });
            });

            // 监测面板数据项点击
            document.querySelectorAll('.data-item').forEach(item => {
                item.addEventListener('click', function(e) {
                    e.preventDefault();
                    redirectToSurvey();
                });
            });

            // 成功案例卡片点击
            document.querySelectorAll('.case-card').forEach(card => {
                card.addEventListener('click', function(e) {
                    e.preventDefault();
                    redirectToSurvey();
                });
            });

            // 平台优势卡片点击
            document.querySelectorAll('.advantage-card').forEach(card => {
                card.addEventListener('click', function(e) {
                    e.preventDefault();
                    redirectToSurvey();
                });
            });

            // 服务卡片整体点击
            document.querySelectorAll('.service-card').forEach(card => {
                // 只在没有点击按钮时触发
                card.addEventListener('click', function(e) {
                    if (!e.target.classList.contains('service-btn')) {
                        e.preventDefault();
                        redirectToSurvey();
                    }
                });
            });
        }

        // 页面加载完成后初始化所有功能
        document.addEventListener('DOMContentLoaded', function() {
            initMobileMenu();
            initAllButtons();
        });

        // 导航项点击效果（桌面端）
        document.querySelectorAll('.nav-item').forEach(item => {
            item.addEventListener('click', function() {
                const navText = this.textContent.trim();
                
                document.querySelectorAll('.nav-item').forEach(nav => nav.classList.remove('active'));
                document.querySelectorAll('.mobile-nav-item').forEach(nav => {
                    if (!nav.textContent.includes('登录')) {
                        nav.classList.remove('active');
                    }
                });
                
                this.classList.add('active');
                
                // 同步移动端导航状态
                document.querySelectorAll('.mobile-nav-item').forEach(nav => {
                    if (nav.getAttribute('data-nav') === navText || nav.textContent.trim() === navText) {
                        nav.classList.add('active');
                    }
                });
                
                // 跳转到问卷
                redirectToSurvey();
            });
        });

        // 窗口尺寸变化时关闭移动端菜单
        window.addEventListener('resize', function() {
            if (window.innerWidth > 768) {
                const mobileMenuToggle = document.getElementById('mobileMenuToggle');
                const mobileNav = document.getElementById('mobileNav');
                if (mobileMenuToggle && mobileNav) {
                    mobileMenuToggle.classList.remove('active');
                    mobileNav.classList.remove('active');
                    mobileMenuToggle.setAttribute('aria-label', '打开菜单');
                }
            }
        });

        // 新闻标签切换效果
        document.querySelectorAll('.news-tab').forEach(tab => {
            tab.addEventListener('click', function() {
                document.querySelectorAll('.news-tab').forEach(t => t.classList.remove('active'));
                this.classList.add('active');
            });
        });

        // 数字动画效果
        function animateNumbers() {
            const numbers = document.querySelectorAll('.stat-number, .data-value');
            numbers.forEach(number => {
                const target = parseFloat(number.textContent);
                const increment = target / 50;
                let current = 0;
                
                const timer = setInterval(() => {
                    current += increment;
                    if (current >= target) {
                        current = target;
                        clearInterval(timer);
                    }
                    
                    if (number.textContent.includes('%')) {
                        number.textContent = current.toFixed(1) + '%';
                    } else if (target >= 1000) {
                        number.textContent = current.toFixed(0).replace(/\B(?=(\d{3})+(?!\d))/g, ',');
                    } else {
                        number.textContent = current.toFixed(1);
                    }
                }, 30);
            });
        }

        // 滚动监听，当数字进入视口时开始动画
        const observerOptions = {
            threshold: 0.5,
            rootMargin: '0px 0px -100px 0px'
        };

        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    animateNumbers();
                    observer.unobserve(entry.target);
                }
            });
        }, observerOptions);

        document.querySelectorAll('.stats-dashboard, .monitoring-panel').forEach(el => {
            observer.observe(el);
        });

        // 平滑滚动
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({
                        behavior: 'smooth',
                        block: 'start'
                    });
                }
            });
        });

        // 返回顶部功能
        const backToTop = document.createElement('div');
        backToTop.innerHTML = '↑';
        backToTop.style.cssText = `
            position: fixed;
            bottom: 30px;
            right: 30px;
            width: 50px;
            height: 50px;
            background: linear-gradient(135deg, #0066cc 0%, #3d8bff 100%);
            color: white;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            font-size: 20px;
            font-weight: bold;
            box-shadow: 0 4px 15px rgba(0,102,204,0.3);
            transition: all 0.3s ease;
            opacity: 0;
            visibility: hidden;
            z-index: 1000;
        `;

        document.body.appendChild(backToTop);

        window.addEventListener('scroll', function() {
            if (window.pageYOffset > 300) {
                backToTop.style.opacity = '1';
                backToTop.style.visibility = 'visible';
            } else {
                backToTop.style.opacity = '0';
                backToTop.style.visibility = 'hidden';
            }
        });

        backToTop.addEventListener('click', function() {
            window.scrollTo({
                top: 0,
                behavior: 'smooth'
            });
        });

        backToTop.addEventListener('mouseenter', function() {
            this.style.transform = 'translateY(-3px) scale(1.1)';
            this.style.boxShadow = '0 8px 25px rgba(0,102,204,0.4)';
        });

        backToTop.addEventListener('mouseleave', function() {
            this.style.transform = 'translateY(0) scale(1)';
            this.style.boxShadow = '0 4px 15px rgba(0,102,204,0.3)';
        });
    </script>
</body>
</html>-item">
                                <div class="data-value">8.2%</div>
                                <div class="data-label">GDP增长率</div>
                                <div class="growth-indicator">↑ 同比增长 2.1%</div>
                            </div>
                            <div class="data-item">
                                <div class="data-value">1,267</div>
                                <div class="data-label">固定资产投资（亿元）</div>
                                <div class="growth-indicator">↑ 同比增长 11.5%</div>
                            </div>
                            <div class="data-item">
                                <div class="data-value">894</div>
                                <div class="data-label">外贸出口（亿元）</div>
                                <div class="growth-indicator">↑ 同比增长 15.3%</div>
                            </div>
                            <div class="data-item">
                                <div class="data-value">453</div>
                                <div class="data-label">财政收入（亿元）</div>
                                <div class="growth-indicator">↑ 同比增长 12.8%</div>
                            </div>
                        </div>
                    </div>
                    
                    <div class="monitoring-panel">
                        <h3 class="panel-title">企业运营状况</h3>
                        <div class="data-grid">
                            <div class="data-item">
                                <div class="data-value">8,765</div>
                                <div class="data-label">注册企业数量</div>
                                <div class="growth-indicator">↑ 新增 6.4%</div>
                            </div>
                            <div class="data
