# 智能 OCR 交易数据提取器

一个基于 EasyOCR 的智能交易数据图像识别和提取工具，能够自动识别银行流水、支付截图等图像中的交易信息，并导出为 Excel 格式。

## ✨ 功能特点

- 🔍 **智能 OCR 识别**: 使用 EasyOCR 进行高精度文字识别
- 📊 **交易数据提取**: 自动提取交易时间、金额、余额、支付方式等信息
- 🏷️ **智能分类**: 自动识别交易类型（餐饮、购物、交通、医疗等）
- 📈 **数据导出**: 支持 Excel 格式导出，包含多个统计工作表
- 🖼️ **图像预处理**: 自动优化图像质量，提高识别准确率
- 📁 **批量处理**: 支持批量处理多张图像

## 🚀 快速开始

### 环境要求

- Python 3.7+
- Windows/Linux/macOS

### 安装依赖

```bash
pip install -r requirements.txt
```

### 使用方法

1. **准备图像文件**

   - 将需要识别的图像放入 `input_images` 文件夹
   - 支持格式：PNG, JPG, JPEG, BMP, TIFF, WebP

2. **运行程序**

   ```bash
   python smart_ocr.py
   ```

3. **查看结果**
   - 结果文件保存在 `output` 文件夹中
   - 默认文件名：`smart_transactions.xlsx`

### 命令行参数

```bash
python smart_ocr.py --input input_images --output my_transactions.xlsx --verbose
```

- `--input, -i`: 输入图像目录路径（默认：input_images）
- `--output, -o`: 输出 Excel 文件名（默认：smart_transactions.xlsx）
- `--verbose, -v`: 显示详细输出信息

## 📁 项目结构

```
bill-ocr/
├── input_images/          # 输入图像文件夹
├── output/                # 输出结果文件夹
├── smart_ocr.py          # 主程序文件
├── requirements.txt       # 依赖包列表
└── README.md             # 项目说明文档
```

## 🔧 核心功能

### 交易类型识别

- **还款类**: 还车贷、还房贷、还信用卡等
- **转账类**: 微信转账、支付宝转账等
- **餐饮类**: 外卖、餐厅、奶茶、咖啡等
- **购物类**: 淘宝、京东、商场、超市等
- **交通类**: 打车、公交、地铁、高铁等
- **娱乐类**: 电影、游戏、KTV、酒吧等
- **医疗类**: 医院、诊所、药店、药品等
- **教育类**: 学费、培训、课程、考试等
- **住房类**: 房租、水电费、物业费等
- **投资理财**: 基金、股票、保险、存款等
- **收入类**: 工资、奖金、退款、返现等

### 数据字段

- 交易时间
- 交易类型
- 主要标题
- 副标题
- 金额
- 余额
- 支付方式
- 关联账户

## 📊 输出格式

Excel 文件包含以下工作表：

1. **交易记录**: 所有识别的交易数据
2. **数据摘要**: 交易统计信息
3. **数据质量报告**: 各字段完整性分析
4. **交易类型统计**: 按类型分类统计
5. **支付方式统计**: 按支付方式分类统计

## 🛠️ 技术架构

- **OCR 引擎**: EasyOCR (支持中英文识别)
- **图像处理**: OpenCV + Pillow
- **数据处理**: Pandas + NumPy
- **数据导出**: OpenPyXL

## 📝 使用示例

### 基本使用

```python
from smart_ocr import SmartOCRExtractor

# 创建提取器实例
extractor = SmartOCRExtractor()

# 处理单张图像
transactions = extractor.process_image("path/to/image.jpg")

# 批量处理
all_transactions = extractor.batch_process("input_images/")

# 导出到Excel
extractor.export_to_excel(all_transactions, "output.xlsx")
```

### 自定义配置

```python
# 自定义交易类型识别模式
extractor.transaction_patterns['自定义类型'] = {
    'keywords': ['关键词1', '关键词2'],
    'patterns': [r'正则表达式1', r'正则表达式2'],
    'priority': 1
}
```

## 🔍 故障排除

### 常见问题

1. **EasyOCR 安装失败**

   ```bash
   pip install easyocr --upgrade
   ```

2. **图像识别效果差**

   - 确保图像清晰度足够
   - 检查图像是否包含完整文字信息
   - 尝试调整图像亮度和对比度

3. **内存不足**
   - 减少同时处理的图像数量
   - 关闭其他占用内存的程序

### 性能优化

- 使用 GPU 加速（需要安装 PyTorch）
- 调整 OCR 置信度阈值
- 优化图像预处理参数

## 📄 许可证

本项目采用 MIT 许可证，详见 LICENSE 文件。

## 🤝 贡献

欢迎提交 Issue 和 Pull Request 来改进这个项目！

## 📞 联系方式

如有问题或建议，请通过以下方式联系：

- 提交 GitHub Issue
- 发送邮件至：[lizx381@gmail.com]

---

**注意**: 本工具仅用于学习和个人使用，请遵守相关法律法规和隐私政策。
