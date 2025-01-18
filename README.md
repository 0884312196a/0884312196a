import networkx as nx
import matplotlib.pyplot as plt

# สร้างกราฟ (Graph)
G = nx.DiGraph()  # ใช้ DiGraph เพราะต้องการให้ลูกศรแสดงทิศทางความสัมพันธ์

# เพิ่มโหนดและความสัมพันธ์ (Add Nodes and Edges)
G.add_edges_from([
    ("Stroke Volume (SV)", "Cardiac Output (CO)"),  # SV เพิ่มส่งผลต่อ CO
    ("Stroke Volume (SV)", "Pulse Pressure"),       # SV เพิ่มส่งผลต่อ Pulse Pressure
    ("Heart Rate (HR)", "Cardiac Output (CO)"),     # HR เพิ่มส่งผลต่อ CO
    ("Heart Rate (HR)", "RR-Interval (ECG)"),       # HR เพิ่มลด RR-Interval
    ("Heart Rate (HR)", "AV Node Delay"),           # HR เพิ่มลด AV Node Delay
    ("Cardiac Output (CO)", "Systolic Blood Pressure"),  # CO เพิ่มส่งผลต่อ Systolic BP
    ("Systolic Blood Pressure", "Pulse Pressure"),  # Systolic BP เพิ่มส่งผลต่อ Pulse Pressure
    ("Sympathetic NS", "Heart Rate (HR)"),          # Sympathetic NS กระตุ้น HR
    ("Sympathetic NS", "Stroke Volume (SV)"),       # Sympathetic NS กระตุ้น SV
    ("Sympathetic NS", "Vasoconstriction"),         # Sympathetic NS กระตุ้น Vasoconstriction
    ("Parasympathetic NS", "Heart Rate (HR)"),      # Parasympathetic NS ลด HR
    ("Vasodilation", "Total Peripheral Resistance (TPR)"),  # Vasodilation ลด TPR
    ("Vasoconstriction", "Total Peripheral Resistance (TPR)"),  # Vasoconstriction เพิ่ม TPR
    ("Venous Return", "Stroke Volume (SV)")         # Venous Return เพิ่มส่งผลต่อ SV
])

# ตำแหน่งของโหนดในกราฟ (Layout of the Graph)
pos = nx.spring_layout(G)  # ใช้ spring layout เพื่อการจัดเรียงโหนดที่สวยงาม

# วาดกราฟ (Draw the Graph)
plt.figure(figsize=(12, 8))  # ตั้งขนาดของกราฟ
nx.draw_networkx_nodes(
    G, pos, node_size=2000, node_color="white", edgecolors="black"
)  # วาดโหนด (วงกลม) ให้ไม่มีสี แต่มีขอบดำ
nx.draw_networkx_edges(
    G, pos, arrowstyle="->", arrowsize=20, edge_color="black"
)  # วาดลูกศรแสดงทิศทางความสัมพันธ์ด้วยสีดำ
nx.draw_networkx_labels(G, pos, font_size=10, font_color="black")  # วาดป้ายชื่อโหนดด้วยสีดำ

# ชื่อกราฟ (Graph Title)
plt.title("Parameter Relationships During Exercise (No Color)", fontsize=14)

# ปิดแกนกราฟ (Hide Axis)
plt.axis("off")

# แสดงกราฟ (Display Graph)
plt.show()
