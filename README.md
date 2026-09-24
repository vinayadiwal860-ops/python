from datetime import date

tasks = []


def add_task():
    subject = input("Enter subject: ")
    task = input("Enter study task: ")

    tasks.append({
        "subject": subject,
        "task": task,
        "completed": False
    })

    print("✅ Task added successfully!")


def show_tasks():
    if not tasks:
        print("\n📚 No study tasks yet.")
        return

    print("\n--- YOUR STUDY TASKS ---")

    for i, task in enumerate(tasks, 1):
        status = "✅ Done" if task["completed"] else "⏳ Pending"

        print(
            f"{i}. [{status}] "
            f"{task['subject']} - {task['task']}"
        )


def complete_task():
    show_tasks()

    if not tasks:
        return

    try:
        number = int(input("\nEnter task number to complete: "))

        if 1 <= number <= len(tasks):
            tasks[number - 1]["completed"] = True
            print("🎉 Task completed!")
        else:
            print("❌ Invalid task number.")

    except ValueError:
        print("❌ Please enter a number.")


def show_progress():
    if not tasks:
        print("\n📊 No tasks available.")
        return

    completed = sum(task["completed"] for task in tasks)
    total = len(tasks)

    progress = (completed / total) * 100

    print("\n📊 STUDY PROGRESS")
    print(f"Completed: {completed}/{total}")
    print(f"Progress: {progress:.1f}%")


def main():
    print("================================")
    print("       PYTHON STUDY MATE")
    print("================================")
    print(f"Today: {date.today()}")

    while True:
        print("\n1. Add Study Task")
        print("2. View Tasks")
        print("3. Complete Task")
        print("4. Show Progress")
        print("5. Exit")

        choice = input("\nChoose an option: ")

        if choice == "1":
            add_task()

        elif choice == "2":
            show_tasks()

        elif choice == "3":
            complete_task()

        elif choice == "4":
            show_progress()

        elif choice == "5":
            print("\n👋 Keep learning Python!")
            break

        else:
            print("❌ Invalid choice.")


if __name__ == "__main__":
    main()
