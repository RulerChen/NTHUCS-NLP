# NTHU NLP HW1

## Environment

- Python 3.10.11
- CPU i5-12400

## Install

- 開啟虛擬環境

```bash
python -m venv myenv
```

- 在 windows powershell 中進入虛擬環境

```bash
./myenv/Scripts/activate.ps1
```

- 安裝套件

```bash
pip install -r requirements.txt
```

- 將需要的檔案放在根目錄中

- `question-words.txt`
- `wiki_texts_part_*.txt` : * = 0-10

- 需要依據註解修改成 pwsh 命令並執行 :

取代 `wget http://download.tensorflow.org/data/questions-words.txt`

```pwsh
Invoke-WebRequest -Uri "http://download.tensorflow.org/data/questions-words.txt" -OutFile "question-words.txt"
```

取代 `cat wiki_texts_part_*.txt > wiki_texts_combined.txt`

```pwsh
0..10 | ForEach-Object { Get-Content "wiki_texts_part_$_.txt" } | Set-Content "wiki_texts_combined.txt"
```

取代 `head -n 10 wiki_texts_combined.txt`

```pwsh
Get-Content "wiki_texts_combined.txt" | Select-Object -First 10 
```

依據測試，前處理的資料約需要 70-80 分鐘，訓練約需要 30 分鐘
