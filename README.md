# FTK-Imager_2
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
    <title>FTK Imager Report</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            -webkit-tap-highlight-color: transparent;
        }
        
        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
            line-height: 1.6;
            color: #333;
            background: #f5f5f7;
            padding: 0;
            overflow-x: hidden;
        }
        
        .container {
            max-width: 100%;
            background: white;
        }
        
        .header {
            background: linear-gradient(135deg, #1e3c72 0%, #2a5298 100%);
            color: white;
            padding: 40px 20px;
            text-align: center;
            position: sticky;
            top: 0;
            z-index: 100;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }
        
        .header h1 {
            font-size: 1.8em;
            margin-bottom: 8px;
            font-weight: 600;
        }
        
        .header p {
            font-size: 0.95em;
            opacity: 0.9;
        }
        
        .author {
            font-size: 1em;
            margin-top: 10px;
            opacity: 0.95;
            font-style: italic;
        }
        
        .content {
            padding: 20px 15px;
        }
        
        .section {
            margin-bottom: 25px;
            padding: 20px 15px;
            background: white;
            border-radius: 12px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.08);
        }
        
        .section h2 {
            color: #1e3c72;
            font-size: 1.4em;
            margin-bottom: 15px;
            padding-bottom: 10px;
            border-bottom: 2px solid #2a5298;
            font-weight: 600;
        }
        
        .section h3 {
            color: #2a5298;
            font-size: 1.15em;
            margin: 15px 0 10px 0;
            font-weight: 600;
        }
        
        .section p {
            margin-bottom: 12px;
            font-size: 0.95em;
            line-height: 1.7;
        }
        
        .section ul, .section ol {
            margin-left: 20px;
            margin-top: 10px;
            padding-left: 5px;
        }
        
        .section li {
            margin-bottom: 10px;
            font-size: 0.95em;
            line-height: 1.6;
        }
        
        .highlight-box {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 18px;
            border-radius: 10px;
            margin: 15px 0;
        }
        
        .highlight-box h3 {
            color: white;
            font-size: 1.1em;
            margin-bottom: 12px;
        }
        
        .highlight-box ul {
            list-style: none;
            margin: 0;
            padding: 0;
        }
        
        .highlight-box li {
            padding-left: 25px;
            position: relative;
            margin-bottom: 10px;
            font-size: 0.9em;
        }
        
        .highlight-box li:before {
            content: "✓";
            position: absolute;
            left: 0;
            font-weight: bold;
            font-size: 1.2em;
        }
        
        .note {
            background: #fff3cd;
            border-left: 4px solid #ffc107;
            padding: 12px 15px;
            margin: 12px 0;
            border-radius: 6px;
            font-size: 0.95em;
        }
        
        .note strong {
            color: #000;
            display: block;
            margin-bottom: 5px;
            font-weight: 700;
        }
        
        .note-text {
            color: #000;
            font-weight: 500;
        }
        
        .link {
            color: #2a5298;
            text-decoration: none;
            font-weight: 500;
            word-break: break-all;
            font-size: 0.85em;
            display: inline-block;
            padding: 8px 0;
        }
        
        .table-container {
            overflow-x: auto;
            -webkit-overflow-scrolling: touch;
            margin: 15px -15px;
            padding: 0 15px;
        }
        
        table {
            width: 100%;
            min-width: 600px;
            border-collapse: collapse;
            margin: 15px 0;
            background: white;
            box-shadow: 0 2px 8px rgba(0,0,0,0.08);
            border-radius: 8px;
            overflow: hidden;
            font-size: 0.85em;
        }
        
        th {
            background: linear-gradient(135deg, #1e3c72 0%, #2a5298 100%);
            color: white;
            padding: 12px 10px;
            text-align: left;
            font-weight: 600;
            font-size: 0.9em;
        }
        
        td {
            padding: 10px;
            border-bottom: 1px solid #e0e0e0;
            line-height: 1.5;
            color: #000;
            font-weight: 500;
        }
        
        .footer {
            background: #1e3c72;
            color: white;
            text-align: center;
            padding: 25px 15px;
            font-size: 0.85em;
        }
        
        .scroll-hint {
            text-align: center;
            color: #666;
            font-size: 0.8em;
            margin: 10px 0;
            font-style: italic;
        }
        
        @media (max-width: 414px) {
            .header h1 {
                font-size: 1.5em;
            }
            
            .section h2 {
                font-size: 1.25em;
            }
            
            .section h3 {
                font-size: 1.05em;
            }
            
            .section p, .section li {
                font-size: 0.9em;
            }
        }
        
        @media (prefers-color-scheme: dark) {
            body {
                background: #1c1c1e;
            }
            
            .section {
                background: #2c2c2e;
                color: #f5f5f7;
            }
            
            .section h2, .section h3 {
                color: #0a84ff;
            }
            
            .section p, .section li {
                color: #e5e5e7;
            }
            
            td {
                border-bottom-color: #48484a;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>FTK Imager</h1>
            <p>Digital Forensics Tool</p>
            <p class="author">by Reema ALJumhur</p>
        </div>
        
        <div class="content">
            <div class="section">
                <h2>Introduction</h2>
                <p>FTK Imager is considered one of the most important tools used in the field of Digital Forensics. The program is used to copy and preserve digital evidence from devices in a secure manner that ensures no tampering occurs, making it an essential tool in security incident investigations, data recovery, and suspicious file analysis.</p>
            </div>
            
            <div class="section">
                <h2>Program Concept and Benefits</h2>
                <p>FTK Imager creates an identical image copy of hard drives, original files, CDs, or DVDs without modifying them.</p>
                
                <div class="highlight-box">
                    <h3>Key Benefits:</h3>
                    <ul>
                        <li>Preserve original digital evidence without any alterations</li>
                        <li>Analyze deleted or hidden data within disks</li>
                        <li>Recover corrupted or lost files</li>
                        <li>Examine virus-infected disks without running them directly</li>
                    </ul>
                </div>
                
                <h3>Essential Tool For:</h3>
                <ul>
                    <li>Digital forensic investigations</li>
                    <li>Cybersecurity</li>
                    <li>Technical support and data recovery</li>
                </ul>
            </div>
            
            <div class="section">
                <h2>How to Download</h2>
                <ol>
                    <li>Navigate to the official Access Data website:<br>
                    <a href="https://www.exterro.com/downloads/search-results?q=&category=64914" class="link">Download FTK Imager</a></li>
                    <li>Select the appropriate version for your system (typically Windows)</li>
                    <li>Run directly without installation (Portable)</li>
                </ol>
            </div>
            
            <div class="section">
                <h2>How to Operate</h2>
                
                <h3>1. Opening the Program</h3>
                <p>After launching, the interface contains:</p>
                <ul>
                    <li><strong>File:</strong> Add data source</li>
                    <li><strong>View:</strong> Browse files</li>
                    <li><strong>Evidence Tree:</strong> Display evidence structure</li>
                </ul>
                
                <h3>2. Creating a Disk Copy</h3>
                <ol>
                    <li>Select <strong>File → Create Disk Image</strong></li>
                    <li>Choose source type:
                        <ul>
                            <li>Physical Drive</li>
                            <li>Logical Drive</li>
                            <li>Image File</li>
                            <li>Contents of a Folder</li>
                        </ul>
                    </li>
                    <li>Select disk or folder</li>
                    <li>Specify file type (E01 or RAW)</li>
                    <li>Set destination path and name</li>
                </ol>
                
                <div class="note">
                    <strong>Important Note:</strong>
                    <span class="note-text">The copy destination should be on a different drive than the one being copied.</span>
                </div>
            </div>
            
            <div class="section">
                <h2>Adding Evidence Items</h2>
                <ol>
                    <li>Select <strong>File → Add Evidence Item</strong></li>
                    <li>Choose <strong>Image File</strong></li>
                    <li>Click <strong>Next</strong></li>
                    <li>Specify the image file</li>
                    <li>Evidence appears in <strong>Evidence Tree</strong></li>
                </ol>
            </div>
            
            <div class="section">
                <h2>File Preview</h2>
                <ul>
                    <li>View contents in lower interface section</li>
                    <li>Deleted data marked with X</li>
                    <li>Right-click and select <strong>Export File</strong> to recover</li>
                </ul>
            </div>
            
            <div class="section">
                <h2>Key Features</h2>
                <div class="highlight-box">
                    <ul>
                        <li>Free and easy to use</li>
                        <li>Recovers permanently deleted files</li>
                        <li>Supports NTFS, FAT, exFAT, EXT</li>
                        <li>Creates Hash Values (MD5, SHA1)</li>
                    </ul>
                </div>
            </div>
            
            <div class="section">
                <h2>Types of Digital Images</h2>
                <p class="scroll-hint">← Swipe to see full table →</p>
                <div class="table-container">
                    <table>
                        <thead>
                            <tr>
                                <th>Type</th>
                                <th>Description</th>
                                <th>Usage</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td><strong>Physical Image</strong></td>
                                <td>Complete copy including all data, partitions, and hidden content</td>
                                <td>Precise digital investigations</td>
                            </tr>
                            <tr>
                                <td><strong>Logical Image</strong></td>
                                <td>Copy of files and units only, no unallocated space</td>
                                <td>Routine tasks and specific file tracking</td>
                            </tr>
                            <tr>
                                <td><strong>Image File</strong></td>
                                <td>Previously created digital image</td>
                                <td>Reopening collected evidence</td>
                            </tr>
                            <tr>
                                <td><strong>Folder Contents</strong></td>
                                <td>Specific folder analysis</td>
                                <td>Examining suspicious files</td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>
            
            <div class="section">
                <h2>IT Technical Support Uses</h2>
                <ol>
                    <li>Recovering deleted data</li>
                    <li>Examining damaged or infected drives</li>
                    <li>Documenting security breaches</li>
                    <li>Analyzing suspicious files safely</li>
                </ol>
            </div>
        </div>
        
        <div class="footer">
            <p>FTK Imager Report - Digital Forensics</p>
            <p>© 2025</p>
        </div>
    </div>
</body>
</html>
ا
