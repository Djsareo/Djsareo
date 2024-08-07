import matplotlib.pyplot as plt
from matplotlib.backends.backend_pdf import PdfPages
import numpy as np

# 楽譜の作成
fig, ax = plt.subplots(figsize=(8.5, 11))

# 楽譜のタイトル
ax.text(0.5, 0.95, 'Debussy Style Composition', ha='center', va='center', fontsize=20)

# 楽譜のスタッフ線を描画
staff_lines = np.linspace(0.1, 0.9, 5)
for i in range(4):  # 4段の楽譜
    for line in staff_lines:
        ax.plot([0.1, 0.9], [line - i*0.2, line - i*0.2], color='black')

# 音符の配置
notes = [
    ('C4', 0.125), ('D4', 0.175), ('E4', 0.225), ('G4', 0.275), ('A4', 0.325), ('B4', 0.375),  # 1小節
    ('E4', 0.425), ('G#4', 0.475),  # 2小節
    ('D4', 0.525), ('F#4', 0.575), ('A4', 0.625),  # 3小節
    ('C4', 0.675), ('E4', 0.725), ('G4', 0.775),  # 4小節
    ('D4', 0.825), ('F#4', 0.875), ('A4', 0.925),  # 5小節
    ('E4', 0.975), ('G4', 1.025), ('B4', 1.075),  # 6小節
    ('C#4', 1.125), ('E4', 1.175), ('G#4', 1.225),  # 7小節
    ('Rest', 1.275), ('A4', 1.325), ('Rest', 1.375), ('C5', 1.425),  # 8小節
    ('Rest', 1.475), ('G4', 1.525), ('Rest', 1.575), ('B4', 1.625),  # 9小節
    ('C4', 1.675), ('D4', 1.725), ('E4', 1.775), ('G4', 1.825), ('A4', 1.875), ('B4', 1.925),  # 10小節
    ('E4', 1.975), ('G#4', 2.025),  # 11小節
    ('D4', 2.075), ('F#4', 2.125), ('A4', 2.175),  # 12小節
    ('C4', 2.225), ('E4', 2.275), ('G4', 2.325),  # 13小節
    ('D4', 2.375), ('F#4', 2.425), ('A4', 2.475),  # 14小節
    ('E4', 2.525), ('G4', 2.575), ('B4', 2.625),  # 15小節
    ('C#4', 2.675), ('E4', 2.725), ('G#4', 2.775),  # 16小節
]

# 音符を配置
for note, position in notes:
    if note != 'Rest':
        ax.text(position, 0.5, note, ha='center', va='center', fontsize=14)
    else:
        ax.text(position, 0.5, 'Rest', ha='center', va='center', fontsize=14, color='gray')

# 軸の設定
ax.set_xlim(0, 1)
ax.set_ylim(0, 1)
ax.axis('off')

# PDFとして保存
pdf_path = '/mnt/data/debussy_style_composition.pdf'
with PdfPages(pdf_path) as pdf:
    pdf.savefig(fig)

plt.close(fig)
pdf_path
