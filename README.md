
import tkinter as tk
from tkinter import messagebox
from PIL import Image, ImageTk #Import Image and ImageTk for handling image display in tkinter.

class TipCalculatorGUI:
    def __init__(self, total_amount, calculate_tip, tip_percentage, party_size):
        self.window = tk.Tk()
        self.window.title("Tippy")
        self.total = total_amount
        self.tip = calculate_tip
        self.tip_percentage = tip_percentage
        self.party_size = party_size
        
        #  window
        self.label_amount = tk.Label(self.window, text="Enter total amount:")
        self.label_amount.grid(row=0, column=0)

        self.entry_amount = tk.Entry(self.window)
        self.entry_amount.grid(row=0, column=1)

        self.label_percentage = tk.Label(self.window, text="Tip Percentage:")
        self.label_percentage.grid(row=1, column=0)

        self.entry_percentage = tk.Entry(self.window)
        self.entry_percentage.grid(row=1, column=1)

        self.label_amount = tk.Label(self.window, text = "Party size:")
        self.label_amount.grid(row=2, column=0)

        self.entry_amount = tk.Entry(self.window)
        self.entry_amount.grid(row=2, column=1)





#calculate button
    self.calculate_button = tk.Button(self.window, text="Calculate Tip", command=self.calculate_tip)
    self.calculate_button.grid(row=3, column=0, columnspan=2)

        # Preset 15% button
    self.calculate_15_button = tk.Button(self.window, text="Calculate 15% Tip", command=self.calculate_15_tip)
    self.calculate_15_button.grid(row=4,column=0, columnspan=2)

        # Preset 18% Button
    self.calculate_18_button = tk.Button(self. window, text= "Calculate 18% Tip", command=self.calculate_18_button)
    self.calculate_18_button.grid(row=5, column=0, columnspan=2)


        #reset button
    self.reset_button = tk.Button(self.window, text="reset", command=self.window.quit)
    self.reset_button.grid(row=6,column=0, columnspan=2)

  #load and display a JPEG image
    img = Image.open("C:/Users/egarc/OneDrive/Documents/tipjar.jpg").resize((150, 150), Image.LANCZOS)
    photo = ImageTk.PhotoImage(img) #convert the image to a format suitable for tkinter
    img_label = tk.Label(self.window, image=photo) #create a label to display the image
    img_label.image = photo # keep a reference to avoid the image being garbage collected
    img_label.pack(row=7,column=0, columnspan=2) #pack the image label into the main window

#load and display a JPEG image
    img = Image.open("C:/Users/egarc/OneDrive/Documents/chocolatecoins.jpg").resize((150, 150), Image.LANCZOS)
    photo = ImageTk.PhotoImage(img) #convert the image to a format suitable for tkinter
    img_label = tk.Label(self.window, image=photo) #create a label to display the image
    img_label.image = photo # keep a reference to avoid the image being garbage collected
    img_label.pack(row=8,column=0, columnspan=2) #pack the image label into the main window
  
    def calculate_tip(self):
            bill = float(self.entry_amount.get())
            percentage = float(self.entry_percentage.get())
            tip_percentage = calculate_tip(bill, percentage)
            total_amount = total_amount(bill, tip_percentage)
            self.show_results(tip_percentage, total_amount)

    def calculate_15_tip(self):
            bill = float(self.entry_amount.get())
            percentage = 15
            tip_percentage = calculate_tip(bill, percentage)
            total_amount = total_amount(bill, tip_percentage)
            self.show_results(tip_percentage, total_amount)

    def calculate_18_tip(self):
            bill = float(self.entry_amount.get())
            percentage = 18
            tip_percentage = calculate_tip(bill, percentage)
            total_amount = total_amount(bill, tip_percentage)
            self.show_results(tip_percentage, total_amount)
         



    def show_results(self, tip, total):
        results_window = tk.Toplevel(self.window)
        results_window.title("Calculation Results")

        result_label = tk.Label(results_window, text=f"Tip: ${tip:.2f}\nTotal: ${total:.2f}")
        result_label.pack()

        close_button = tk.Button(results_window, text="Close", command=results_window.destroy)
        close_button.pack()

    def run(self):
        self.window.mainloop()
