# SCGP · Claude Lab Guides

**GitHub Pages**
- Claude for Technician: https://sirasit-b.github.io/scgp-claude-lab-guides/Claude_for_Technician_Lab_Guide.html
- Claude for Researcher: https://sirasit-b.github.io/scgp-claude-lab-guides/Claude_for_Researcher_Lab_Guide.html

คู่มือ Lab สำหรับหลักสูตร Claude (1 วัน) ของ SCGP (IPDC) จัดทำโดย BorntoDev

| คู่มือ | เปิดดูออนไลน์ | โฟลเดอร์ไฟล์ Workshop |
|---|---|---|
| Claude for Technician | [Claude_for_Technician_Lab_Guide.html](https://sirasit-b.github.io/scgp-claude-lab-guides/Claude_for_Technician_Lab_Guide.html) | [SCGP-Technician-Labs](https://drive.google.com/drive/folders/1JMJoGsHR0dtQM2HdgYkxseXr_yjLkAHA) |
| Claude for Researcher | [Claude_for_Researcher_Lab_Guide.html](https://sirasit-b.github.io/scgp-claude-lab-guides/Claude_for_Researcher_Lab_Guide.html) | [SCGP-Researcher-Labs](https://drive.google.com/drive/folders/1_2GS2JWi0LDRtOjZrZWeEnYRslbVCCrS) |

ไฟล์ Workshop อยู่บน Google Drive (ดาวน์โหลดทั้งโฟลเดอร์เป็น .zip แล้วแตกไฟล์ไว้ในเครื่อง) ทุกไฟล์เป็น Mock Document / Dataset ไม่ใช่ข้อมูลจริงขององค์กร

## โครงสร้างโฟลเดอร์ (ใช้เหมือนกันทั้ง 2 หลักสูตร)

แต่ละ Lab เปิดเป็น Cowork Project แยกกัน 1 โฟลเดอร์ต่อ 1 Lab

| โฟลเดอร์ย่อย | มีอะไร |
|---|---|
| `src/` | ไฟล์ต้นฉบับของ Lab นั้น (ห้ามแก้) |
| `prev/` | ไฟล์สำรองจาก Lab ก่อนหน้า ใช้เมื่อทำ Lab ก่อนหน้าไม่ทันหรือไม่ครบ (ห้ามแก้) |
| `output/` | Claude สร้างให้ระหว่างทำ Lab เก็บไฟล์ผลลัพธ์ทั้งหมด |
| `skills/` | Claude สร้างให้ใน Lab E เก็บ Skill ที่ทำขึ้น |

---

## SCGP-Technician-Labs

โจทย์ทั้งวัน: ทำชุดเอกสารสำหรับเครื่อง Bursting Strength Tester BTD BST-1400 (รหัส QC-BST-07) ที่ติดตั้งใหม่

### `00_Check/` · ทดสอบเครื่องก่อนวันอบรม
| ไฟล์ | ใช้ทำอะไร |
|---|---|
| `src/Data_Export_2026-10-20.csv` | ข้อมูลส่งออกจากเครื่อง ทดสอบการอ่าน CSV ด้วย Python |
| `src/Spec_Sheet.xlsx` | Spec ของแต่ละเกรด ทดสอบการอ่าน Excel และ Sub Agent |
| `src/keyframe_00-00-36.jpg` | ภาพจากวิดีโอ ทดสอบการอ่านภาพ |

### `LabA/` · Standard & Manual → Work Instruction
| ไฟล์ | ใช้ทำอะไร |
|---|---|
| `src/TestMethod_TM-201.pdf` | วิธีทดสอบ (อ้างอิง [TM]) |
| `src/Manual_BST-1400_EN.pdf` | คู่มือเครื่อง ภาษาอังกฤษ (อ้างอิง [OM]) |
| `src/Datasheet_Consumables.pdf` | Datasheet แผ่นยางและน้ำมัน (อ้างอิง [DS]) |
| `src/WI_Old_BST-001.docx` | WI ฉบับเก่า ใช้เป็นแม่แบบหัวกระดาษและหาจุดที่ต้องแก้ |

ผลลัพธ์: `LabA_WI-QC-BST-002_Draft.docx`, `LabA_PreUse_Checklist_and_Parameters.xlsx`, `LabA_OldWI_Gap_List.xlsx`

### `LabB/` · Video → Work Procedure
| ไฟล์ | ใช้ทำอะไร |
|---|---|
| `src/Video_BST_Demo.mp4` | วิดีโอสาธิตเครื่อง Bursting Strength Tester แบบ Manual Clamping Digital ของ Presto (1:56 นาที) ช่วงใช้งานจริงคือ 00:00:08–00:00:58 ช่วงหลังเป็นโฆษณาบริษัท (ใช้กับ Gemini / NotebookLM) |
| `src/keyframes/` | ภาพนิ่งจากวิดีโอทุก 2 วินาที 26 ภาพ (`keyframe_00-00-08.jpg` … `_00-00-58.jpg`) ชื่อไฟล์คือ Timestamp ชม.-นาที-วินาที |
| `prev/WI_BST-002_Rev00.docx` | WI สำรอง ใช้เมื่อกลุ่มไม่มี WI จาก Lab A ถ้ามี ให้วาง `LabA_WI-QC-BST-002_Draft.docx` ไว้ในโฟลเดอร์นี้ด้วย |

ผลลัพธ์: `LabB_Video_Work_Procedure.docx`, `LabB_Gap_List.xlsx`

### `LabC/` · Test Data → Test Report
| ไฟล์ | ใช้ทำอะไร |
|---|---|
| `src/Data_Export_2026-10-20.csv` | ไฟล์ Export จากเครื่อง QC-BST-07 วันที่ 20 ต.ค. (3 Lot) บรรทัดที่ขึ้นต้นด้วย # เป็นข้อมูลหัวไฟล์ |
| `src/Data_ManualLog_2026-10-21.xlsx` | บันทึกผลกะ B วันที่ 21 ต.ค. (3 Lot) พิมพ์จากใบบันทึกมือ |
| `src/Spec_Sheet.xlsx` | ข้อกำหนดของแต่ละเกรด (Sheet Spec) และกติกาการตัดสิน Lot (Sheet Decision_Rules) |
| `src/Template_TestReport.docx` | แบบฟอร์ม Test Report ของห้องแล็บ |
| `src/TestMethod_TM-201.pdf` | วิธีทดสอบ (ชุดเดียวกับ Lab A) ใช้อ้างอิงเกณฑ์ชิ้นทดสอบที่ใช้ไม่ได้ การคำนวณ และการแปลงหน่วย |

ผลลัพธ์: `LabC_Data_Quality_Log.xlsx`, `LabC_Test_Data_Clean.xlsx`, `LabC_Test_Report_TR-BST-2610.docx`

### `LabD/` · Flowchart, Visual & Training Media
| ไฟล์ | ใช้ทำอะไร |
|---|---|
| `src/WI_BST-002_Rev00.docx` | WI ฉบับอนุมัติ (ฉบับฝึกอบรม) ของเครื่อง QC-BST-07 เป็นแหล่งข้อมูลเดียวของ Lab นี้ |

ผลลัพธ์: `LabD_Flowchart.html`, `LabD_OPL.pptx`, `LabD_Quick_Reference_Card.docx`, `LabD_Training_Slides.pptx`, `LabD_Post_Training_Quiz.docx`

### `LabE/` · Technician Skills Library + Automation
| ไฟล์ | ใช้ทำอะไร |
|---|---|
| `src/Skills_Rules.md` | กติกากลางของ Library: 5 ส่วนที่ Skill ต้องมี, ชื่อ, Owner, Version, ผู้ตรวจรับรอง และตัวอย่าง Skill ที่อนุมัติแล้ว |
| `src/Spec_Sheet.xlsx` | Spec ของแต่ละเกรด (มีทั้ง Burst และ Cobb60) และกติกาการตัดสิน Lot |
| `src/cobb/Guide_COBB-100_EN.pdf` | คู่มือย่อเครื่องทดสอบอีกชนิด (Cobb Tester) สำหรับ Skill Swap |
| `src/cobb/Cobb_Export_2026-10-22.csv` | ผลทดสอบ Cobb60 จำนวน 2 Lot สำหรับ Skill Swap |
| `src/inbox/Export_2026-10-26.csv` … `_2026-10-28.csv` | ผลทดสอบ Bursting Strength 3 วัน (วันละ 2 Lot) โฟลเดอร์ที่ Scheduled Task จะตรวจ |

ผลลัพธ์: `skills/tech-<ชื่อ>/SKILL.md`, `skills/REGISTER.md`, `output/daily_reports/`, `LabE_Dashboard.html`, Scheduled Task 1 งาน

---

## SCGP-Researcher-Labs

### `00_Check/` · ทดสอบเครื่องก่อนวันอบรม
| ไฟล์ | ใช้ทำอะไร |
|---|---|
| `src/DOE_RawData.xlsx` | ผลการทดลอง ทดสอบการอ่าน Excel |
| `src/Spec_Limits.csv` | เกณฑ์ Spec ทดสอบการอ่าน CSV |

### `LabA/` · Literature & Standards Knowledge Base
| ไฟล์ | ใช้ทำอะไร |
|---|---|
| `src/Paper_Arshad2024_Camelina.pdf` · `Paper_Samyn2021_Sunflower.pdf` · `Paper_Shen2021_PVA.pdf` | งานวิจัย 3 ฉบับ |
| `src/Datasheet_EcoShield_Paper.pdf` · `Datasheet_EcoShield_Linerboard.pdf` | Datasheet ผลิตภัณฑ์ 2 ฉบับ |
| `src/TestMethod_RD-TM-300.pdf` | วิธีทดสอบ |
| `src/Market_SEA2026_MOCK.pdf` | รายงานตลาด (Mock) |
| `src/Patents_MOCK.pdf` | สรุปสิทธิบัตร (Mock) |

ผลลัพธ์: `LabA_Source_Index.md`, `LabA_Evidence_Matrix.xlsx`, `LabA_Research_Gap.md`

### `LabB/` · DOE ออกแบบการทดลองที่ทำได้จริง
| ไฟล์ | ใช้ทำอะไร |
|---|---|
| `src/DOE_Constraints.xlsx` | ข้อจำกัดที่เจ้าของงานยืนยันแล้ว: Sheet `DOE_Constraints` (13 หัวข้อ), `Equipment_Limits` (Rod coater, ตู้อบ, ตู้ WVTR), `Cost_per_Run` |
| `prev/LabA_Research_Gap.md` | ผลจาก Lab A (มีไฟล์สำรองให้แล้ว ถ้ากลุ่มทำเสร็จให้วางของตัวเองทับ) |

ผลลัพธ์: `LabB_Run_Sheet.xlsx`, `LabB_DOE_Plan_Rationale.docx`

### `LabC/` · Research Data Pipeline & Statistics
| ไฟล์ | ใช้ทำอะไร |
|---|---|
| `src/DOE_RawData.xlsx` | Sheet `Lab_Results_Raw`: ผล DOE 12 Run (2³ + 4 Center points, 2 Block ตาม Lot กระดาษ) รายค่าซ้ำของ Cobb60, WVTR, KIT มีปัญหาข้อมูลแบบที่พบจริง · `Pilot_Coater_QC`: Pilot trial 25 Subgroup ที่สูตรที่เลือก · `Spec_Limits`: USL/LSL และเกณฑ์ Cpk |
| `src/Cost_Inputs.xlsx` | ราคาวัตถุดิบ (ใบเสนอราคาจำลอง), Process basis, Business case (Capex, ปริมาณขาย, ราคา) |
| `src/TestMethod_RD-TM-300.pdf` | วิธีทดสอบ (ชุดเดียวกับ Lab A) ใช้อ้างอิงเกณฑ์ตัดค่า การแปลงหน่วย และกติกาบันทึกข้อมูล |

ผลลัพธ์: `labC_pipeline.py`, `LabC_Clean_Data.xlsx`, Control chart (`*.png`), `LabC_Cost_Model.xlsx`, `LabC_Analysis_Summary.md`

### `LabD/` · Multi-agent Workflow + Reviewer
| ไฟล์ | ใช้ทำอะไร |
|---|---|
| `src/Patents_MOCK.pdf` | สำหรับ Agent IP |
| `src/Market_SEA2026_MOCK.pdf` | สำหรับ Agent Researcher (Market Fit) |
| `src/Cost_Inputs.xlsx` | สำหรับ Agent Analyst (Financial Case) |
| `src/DOE_RawData.xlsx` | สำหรับ Agent Analyst (เฉพาะเมื่อไม่มีผลจาก Lab C) |
| `prev/LabA_Evidence_Matrix.xlsx` · `LabA_Research_Gap.md` | ผลสำรองจาก Lab A |
| `prev/LabC_Analysis_Summary.md` · `LabC_Cost_Model.xlsx` | ผลสำรองจาก Lab C |

ผลลัพธ์: `LabD_handoff_1_researcher.md`, `LabD_handoff_2_analyst.md`, `LabD_handoff_3_ip.md`, `LabD_Research_Brief.docx`, `LabD_handoff_5_review_log.xlsx`

### `LabE/` · IPDC Skills Library + Automation
| ไฟล์ | ใช้ทำอะไร |
|---|---|
| `src/Skills_Rules.md` | กติกากลาง: 6 ส่วนที่ Skill ต้องมี, ชื่อ, Owner, Version, ผู้ตรวจรับรอง, data_class, ข้อห้ามด้าน Research Integrity และตัวอย่าง Skill |
| `src/Spec_Limits.csv` | USL ของ Cobb60 และ WVTR และเกณฑ์ Cpk |
| `src/weekly_qc/QC_W41.csv` … `QC_W43.csv` | ผล QC ของ Pilot coater รายสัปดาห์ (สัปดาห์ละ 10 Subgroup: Cobb60 n=4, WVTR n=2, Coat weight) โฟลเดอร์ที่ Scheduled Task จะตรวจ |

ผลลัพธ์: `skills/ipdc-<ชื่อ>/SKILL.md`, `skills/REGISTER.md`, `LabE_Research_Watch.html`, `output/weekly_watch/`, Scheduled Task 1 งาน
