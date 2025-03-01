import tkinter as tk
from tkinter import ttk
import keyboard  # Para capturar o pressionamento da tecla P

# Variáveis globais
aimbot_ativo = False
wallhack_ativo = False
fov = 150.0
aimbot_precisao = 100

# Função para alternar Aimbot
def toggle_aimbot():
    global aimbot_ativo
    aimbot_ativo = not aimbot_ativo
    if aimbot_ativo:
        btn_aimbot.config(bg="green")
        slider_precisao.config(state="normal")
    else:
        btn_aimbot.config(bg="red")
        slider_precisao.config(state="disabled")

# Função para ajustar precisão do Aimbot
def update_precisao(value):
    global aimbot_precisao
    aimbot_precisao = int(value)
    lbl_precisao.config(text=f"Precisão: {aimbot_precisao}%")

# Função para ajustar FOV
def update_fov(value):
    global fov
    fov = float(value)
    lbl_fov.config(text=f"FOV: {fov:.2f}")

# Função para alternar Wallhack
def toggle_wallhack():
    global wallhack_ativo
    wallhack_ativo = not wallhack_ativo
    if wallhack_ativo:
        btn_wallhack.config(bg="green")
        btn_skeleton.config(state="normal")
    else:
        btn_wallhack.config(bg="red")
        btn_skeleton.config(state="disabled")

# Função para verificar se a tecla P foi pressionada
def check_key():
    if keyboard.is_pressed('p'):  # Verifica se a tecla P foi pressionada
        open_menu()

# Função para abrir o menu quando a tecla P for pressionada
def open_menu():
    root.deiconify()  # Exibe o menu
    root.after(10, check_key)  # Continua verificando se a tecla P foi pressionada

# Criando a interface principal
root = tk.Tk()
root.title("Z9 Hub : Z9 Menu - by wz99gd")
root.geometry("400x300")
root.withdraw()  # Inicialmente o menu estará escondido

# Criando abas
notebook = ttk.Notebook(root)
aba_aimbot = ttk.Frame(notebook)
aba_wallhack = ttk.Frame(notebook)
notebook.add(aba_aimbot, text="Aimbot")
notebook.add(aba_wallhack, text="Wallhack")
notebook.pack(expand=True, fill="both")

# ---- Aba Aimbot ----
btn_aimbot = tk.Button(aba_aimbot, text="Aimbot", bg="red", command=toggle_aimbot)
btn_aimbot.pack(pady=10)

lbl_precisao = tk.Label(aba_aimbot, text="Precisão: 100%")
lbl_precisao.pack()
slider_precisao = tk.Scale(aba_aimbot, from_=1, to=200, orient="horizontal", command=update_precisao)
slider_precisao.pack()

lbl_fov = tk.Label(aba_aimbot, text="FOV: 150.00")
lbl_fov.pack()
slider_fov = tk.Scale(aba_aimbot, from_=150, to=200, orient="horizontal", resolution=0.01, command=update_fov)
slider_fov.pack()

# ---- Aba Wallhack ----
btn_wallhack = tk.Button(aba_wallhack, text="Wallhack", bg="red", command=toggle_wallhack)
btn_wallhack.pack(pady=10)

btn_skeleton = tk.Butto
