Great! Here's the updated version of your GitHub `README.md` with your **NovyPro project link** included:

---

```markdown
# 🧑‍💼 Dynamic Staff Attendance Dashboard — Power BI

A visually interactive Power BI dashboard for tracking and analyzing employee attendance using scrollable SVG cards, calendar-based matrix visuals, and conditional formatting to identify attendance patterns at a glance.

🔗 **[View Project on NovyPro](https://www.novypro.com/manage_projects/awindanjuma)**

---

## 📊 Project Overview

This dashboard is designed for HR teams, managers, and executives to monitor staff attendance in real time. It includes a scrollable panel of employee cards with embedded profile pictures and dynamic attendance percentages, alongside a calendar matrix that highlights daily attendance status with clear color codes.

---

## 🔧 Features

### ✅ Dynamic Employee Cards
- Scrollable SVG cards per employee
- Display:
  - Name
  - Team
  - Profile picture (circular clipped)
  - Attendance percentage
- Rendered using `DAX + inline SVG` (no custom visuals)

### 📅 Attendance Calendar View
- Matrix visual showing **weekly and monthly** attendance
- Color-coded daily status:
  | Status               | Color       |
  |----------------------|-------------|
  | 🟢 Present           | `#4CAF50`   |
  | 🔴 Absent/Remote/Sick| `#F44336`   |
  | 🔴 Public Holiday    | `#F44336`   |
  | 🟨 Weekend (Sat/Sun) | `#FFEB3B`   |
  | ⚪ Undefined          | `#BDBDBD`   |

### 📈 Attendance KPIs
- Total Days
- Total Attendance
- Working Days
- Attendance %
- Days in Month
- Work Days in Month

### 🧭 Navigation
- Month switch via slicers or bookmarks
- Real-time filtering by team, department, or employee

---

## 🚀 Getting Started

### 🛠 Requirements
- Power BI Desktop (June 2022 or later)
- Your attendance dataset with:
  - `Employee Name`, `Team`, `Profile Picture`, `Status`, and `Date`
  - `Calendar` table with `IsHoliday` and `Weekday` logic

### 📂 Recommended Data Model
```

┌────────────────────┐
│     Attendance     │
│  \[Employee], \[Date], \[Status]  │
└────────────────────┘
▲
│ Many-to-one
▼
┌────────────────────┐
│     Calendar       │
│  \[Date], \[IsHoliday], \[Weekday] │
└────────────────────┘
▲
│
▼
┌────────────────────┐
│     People         │
│  \[Employee], \[Team], \[ImageBytes] │
└────────────────────┘

````

---

## 📦 DAX Samples

### 🎨 Attendance Color Measure
```dax
AttendanceColor = 
VAR dayOfWeek = WEEKDAY('Calendar'[Date], 2)
VAR isWeekend = dayOfWeek IN {6, 7}
VAR isHoliday = SELECTEDVALUE('Calendar'[IsHoliday]) = TRUE
VAR status = SELECTEDVALUE('Attendance Data'[Status])

RETURN
SWITCH(
    TRUE(),
    isHoliday, "#F44336",
    isWeekend, "#FFEB3B",
    status IN {"Sick", "Absent", "Remote"}, "#F44336",
    status = "Present", "#4CAF50",
    "#BDBDBD"
)
````

### 🖼️ SVG Employee Card Snippet

```dax
Emp Card = 
"data:image/svg+xml;utf8," &
"<svg ...>" &  -- full SVG with name, team, % attendance
"</svg>"
```

> Full DAX available in the report.

---

## 📌 To Do / Future Features

* [ ] Tooltip pages for absence reason
* [ ] Export-to-PDF button
* [ ] Department trendlines
* [ ] Mobile layout support

---

## 🧠 Credits

Built by [Awin Danjuma](https://www.novypro.com/manage_projects/awindanjuma) using Power BI, DAX, and SVG.

Icons and color system follow accessibility-friendly standards.

---

## 📄 License

This project is licensed under the MIT License.

```

---

Would you like me to export this as a `.md` file for direct upload to GitHub? Or generate a thumbnail image for your project preview?
```
