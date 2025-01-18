import networkx as nx
import matplotlib.pyplot as plt

# สร้างกราฟ
G = nx.DiGraph()

# เพิ่มโหนดและความสัมพันธ์
G.add_edges_from([
    ("Stroke Volume (SV)", "Cardiac Output (CO)"),
    ("Stroke Volume (SV)", "Pulse Pressure"),
    ("Heart Rate (HR)", "Cardiac Output (CO)"),
    ("Heart Rate (HR)", "RR-Interval (ECG)"),
    ("Heart Rate (HR)", "AV Node Delay"),
    ("Cardiac Output (CO)", "Systolic Blood Pressure"),
    ("Systolic Blood Pressure", "Pulse Pressure"),
    ("Sympathetic NS", "Heart Rate (HR)"),
    ("Sympathetic NS", "Stroke Volume (SV)"),
    ("Sympathetic NS", "Vasoconstriction"),
    ("Parasympathetic NS", "Heart Rate (HR)"),
    ("Vasodilation", "Total Peripheral Resistance (TPR)"),
    ("Vasoconstriction", "Total Peripheral Resistance (TPR)"),
    ("Venous Return", "Stroke Volume (SV)")
])

# ตำแหน่งของโหนดในกราฟ
pos = nx.spring_layout(G)

# วาดกราฟ
plt.figure(figsize=(12, 8))
nx.draw_networkx_nodes(G, pos, node_size=2000, node_color="lightblue")
nx.draw_networkx_edges(G, pos, arrowstyle="->", arrowsize=20, edge_color="gray")
nx.draw_networkx_labels(G, pos, font_size=10, font_color="black")

plt.title("Parameter Relationships During Exercise", fontsize=14)
plt.axis("off")
plt.show()
