---
# Day 06 – Linux Fundamentals: Read and Write Text Files
---

---
## Task
---

---
This is a continuation of **Day 05**, but much simpler.

Today’s goal is to **practice basic file read/write** using only fundamental commands.

You will create a small text file and practice:

- Creating a file
- Writing text to a file
- Appending new lines
- Reading the file back

---
Keep it basic and repeatable.
---

---

Create a file named notes.txt

Write 3 lines into the file using redirection (> and >>)

Use cat to read the full file

Use head and tail to read parts of the file

Use tee once to write and display at the same time

Keep it short (8–12 lines total in the file)

---

---
### To create a file i have used command
---

```bash
touch notes.txt
```
---

---
### To Redirect the test to the notes.txt file 
---

```bash
echo "This is my first line" > notes.txt 
```
---

---
### To append the text to the notes.txt
---

```bash
echo "Added new line to the same file" >> notes.txt
```
---
## To print first two line of file output into the terminal

```bash
head -n 2 notes.txt
```

---
## To print last two line of file output into the terminal
---

```bash
tail -n 2 notes.txt
```
---


<iamge 1>


---
### Using ***tee*** command for direction and apppend
---

```bash
# for redirection
ls -l | tee notes.txt

# For append 
echo "new line" | tee notes.txt

```
<image 2>
---

```
In this task, I learned how to ***redirect text output*** to a file, how to view the first or last lines of a text file using commands like ***head and tail***, and how to use the ***tee*** command to ***append output*** to a file while also displaying it on the terminal.
```
