# Git Branching Strategy 
| สาขา (Branch)      | วัตถุประสงค์ (Purpose)                                                       |
|-------------|-----------------------------------------------------------------|
| `main`      | สำหรับเก็บโค้ดที่เสถียรและพร้อมใช้งานในระบบจริง (production) โดยจะเก็บเวอร์ชันที่ปล่อยให้ใช้งานด้วย  |
| `dev`       | สำหรับการรวมฟีเจอร์ต่าง ๆ และเป็นพื้นที่หลักของการพัฒนา   |
| `hotfix`    | สำหรับการแก้ไขปัญหาสำคัญแบบเร่งด่วนที่นำไปใช้กับระบบจริง (main) โดยตรง      | 
| `release`    | สำหรับทดสอบฟีเจอร์ต่าง ๆที่พัฒนามาก่อนที่จะปล่อยให้ใช้งานในระบบจริง (production)      | 

```mermaid
gitGraph
   commit id: "Init" tag: "v1.0.0"

   branch hotfix
   branch release
   branch dev
   

   checkout dev
   commit id: "Feature 1"
   commit id: "Feature 2"

   checkout hotfix
   commit id: "Fix bugs 1"
   
   checkout dev
   merge hotfix

   checkout main
   merge hotfix
   commit id: "Patch 1" tag: "v1.0.1"

   checkout dev
   commit id: "Feature 3"

   checkout hotfix
   merge main
   commit id: "Fix bugs 2"
   
   checkout dev
   merge hotfix

   checkout main
   merge hotfix
   commit id: "Patch 2" tag: "v1.0.2"

   checkout dev
   commit id: "Feature 4"

   checkout release
   merge dev
   commit id: "Test 1"

   checkout dev
   merge release

   checkout main
   merge release
   commit id: "Release 1" tag: "v1.1.0"

   checkout dev
   commit id: "Feature 5"

   checkout hotfix
   merge main
   commit id: "Fix bugs 3"

   checkout dev
   merge hotfix

   checkout main
   merge hotfix
   commit id: "Patch 3" tag: "v1.1.1"

   checkout dev
   commit id: "Feature 6"
   commit id: "Feature 7"

   checkout release
   merge dev
   commit id: "Test 2"
   commit id: "Test 3"

   checkout dev
   merge release

   checkout main
   merge release
   commit id: "Release 2" tag: "v1.2.0"

```
