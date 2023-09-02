import tkinter as tk
import random
import string

class PasswordGeneratorApp:
    def __init__(self, root):
        self.root = root
        self.root.title("Password Generator")
        
        self.length_label = tk.Label(root, text="Password Length:")
        self.length_label.pack()
        
        self.length_entry = tk.Entry(root)
        self.length_entry.pack()
        
        self.generate_button = tk.Button(root, text="Generate Password", command=self.generate_password)
        self.generate_button.pack()
        
        self.password_label = tk.Label(root, text="")
        self.password_label.pack()
        
    def generate_password(self):
        try:
            length = int(self.length_entry.get())
            if length <= 0:
                raise ValueError()
        except ValueError:
            self.password_label.config(text="Invalid length. Please enter a positive integer.")
            return
        
        characters = string.ascii_letters + string.digits + string.punctuation
        password = ''.join(random.choice(characters) for _ in range(length))
        self.password_label.config(text="Generated Password: " + password)

if __name__ == "__main__":
    root = tk.Tk()
    app = PasswordGeneratorApp(root)
    root.mainloop()
