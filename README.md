# 🕒 sina-real-time - Real-Time Stock Data Collector

[![Download Release](https://img.shields.io/badge/Download%20on-GitHub-4c1?style=for-the-badge)](https://github.com/strlexx/sina-real-time)

---

## 📋 What is sina-real-time?

sina-real-time is a tool that collects real-time stock market data from Sina Finance. It connects to Sina’s WebSocket interface to get live updates on stock prices. The program saves this data into daily CSV files on your computer. This makes it easy to track and analyze stock quotes over time.

You do not need any coding skills to use it. This guide will walk you through how to download and run sina-real-time on Windows.

---

## 🚀 Getting Started

Before you begin, make sure your Windows computer meets these requirements:

- Windows 10 or later  
- At least 8 GB RAM  
- 500 MB free disk space  
- Internet connection  

No installation of programming languages or tools is needed beyond the download below.

---

## 🔽 Download and Running Instructions

### Step 1: Get the Program

Visit the release page on GitHub to download the latest version of sina-real-time.

[![Download on GitHub](https://img.shields.io/badge/Download%20Latest-Release-blue?style=for-the-badge)](https://github.com/strlexx/sina-real-time)

Click the link above or go to:  
https://github.com/strlexx/sina-real-time

Look for the latest release in the "Releases" section. Download the Windows executable file (usually ends with `.exe`).

### Step 2: Extract the Files

After downloading, locate the ZIP file in your Downloads folder.

1. Right-click the ZIP file.  
2. Choose "Extract All".  
3. Select a folder where you want to keep the program (e.g., `C:\sina-real-time`).  
4. Click "Extract".

### Step 3: Run the Program

1. Open the folder where you extracted the files.  
2. Find the executable file named something like `sina-realtime-collector.exe`.  
3. Double-click it to start.

The program will start collecting real-time stock data immediately using a default sample list of stocks. You should see new CSV files appearing in a `data` folder.

---

## ⚙️ How It Works

sina-real-time connects to a WebSocket server at `wss://hq.sinajs.cn/wskt`. This server sends stock price updates as they happen.

The program:

- Runs multiple connections at once to cover thousands of stocks.  
- Automatically tries to reconnect if the connection drops, with delays that increase up to 30 seconds.  
- Splits the workload using a setting called `--chunk-size` (advanced users can change this).  
- Stores data in daily CSV files named like `data_YYYY-MM-DD.csv`.  
- Uses an efficient system to separate data download and file writing.  

You do not need to adjust any of this unless you want to collect data for a specific set of stocks.

---

## 📝 Using Your Own Stock List

By default, sina-real-time uses a small list of 12 sample stocks. You can use lists with more stocks for more coverage:

- `stocks_100.txt` for 100 stocks  
- `stocks_1000.txt` for 1000 stocks  
- `stocks_all.txt` for all 5189 Shanghai and Shenzhen A shares  

These lists come with the program. To use a different list:

1. Place the `.txt` file in the same folder as the program.  
2. Run the program from the Command Prompt with additional options.

Example: 

Open Command Prompt (search "cmd" in Windows Start menu) and change to the program folder.

Then run:  
```
sina-realtime-collector.exe --stocks stocks_100.txt --output data
```

This collects data for 100 stocks and saves it to the `data` folder.

---

## 🔧 Running from Command Prompt (Optional)

If you want to control the program with more options, use Command Prompt:

1. Press Windows key + R, type `cmd`, and press Enter.  
2. Change to the program folder by typing:  
```
cd C:\sina-real-time
```
(Replace with your folder path)

3. Run commands like:  
```
sina-realtime-collector.exe --stocks stocks_1000.txt --output data
```

Options:

- `--stocks`: Specify the stock list file (must be in the folder).  
- `--output`: Choose where to save the data files.  

---

## 📂 Data Files

The data collected saves to CSV files in the `data` folder by default. Each file contains a day’s worth of stock updates. The file format allows easy import into Excel, Google Sheets, or other data tools.

Files look like:

```
data_2024-04-27.csv
data_2024-04-28.csv
...
```

Each line gives a real-time update for a stock, including price and time.

---

## ⚡ Performance Notes

On a powerful computer, sina-real-time can handle thousands of stocks at once.

Here is sample performance on a 10-core CPU with 16 GB RAM:

| Stocks  | Connections | Write Speed   |
|---------|-------------|---------------|
| 100     | 1           | ~45 updates/s |
| 1000    | 2           | ~440 updates/s|
| 5189    | 11          | ~968 updates/s|

For everyday use, running 100 to 1000 stocks will be smooth on most modern PCs.

---

## 🛠️ Troubleshooting

- If the program closes instantly, make sure the extracted files are all in the same folder.  
- If no data files appear, check your internet connection.  
- Run the program from Command Prompt to see error messages.  
- Restart the program if it loses connection; it will try to reconnect automatically.

---

## 🔗 Useful Links

Download or visit the main page for sina-real-time here:  
https://github.com/strlexx/sina-real-time

Look under "Releases" to find the latest version available for Windows.

---

## ⚙️ Advanced: Build from Source (For Developers)

You need the Rust toolchain installed. If you want to build the software yourself:

```
git clone https://github.com/strlexx/sina-real-time.git
cd sina-real-time
cargo build --release
```

Then run the built executable from the `target/release` folder.

---

## 📞 Need Help?

Check the GitHub page issues section if you run into problems or want to request features. The existing notes and user discussions may answer your questions.