# 📚 Sistem Integrat pentru Gestiunea unei Biblioteci (C# / WinForms)

Acest repository conține proiectul realizat pentru disciplina **Programare Orientată pe Obiecte (PAOO)**. Este o aplicație desktop robustă, dezvoltată în **C#** și **Windows Forms**, care facilitează gestionarea completă a unei biblioteci (cărți, autori și utilizatori).

**Autor:** Petrea Andrei (Grupa 22C32B)  
**Tehnologii principale:** C#, .NET Framework, MySQL, ADO.NET

---

## 🌟 Caracteristici Tehnice Deosebite
Spre deosebire de aplicațiile clasice WinForms, o caracteristică tehnică avansată a acestui proiect este **generarea interfeței grafice (UI) complet programatic (din cod)**. Nu au fost utilizate uneltele vizuale de tip Drag-and-Drop din Visual Studio, asigurându-se astfel un control strict asupra instanțierii, randării și adaptării elementelor vizuale în funcție de rolul utilizatorului conectat.

---

## 👥 Funcționalități pe Bază de Roluri (RBAC)

Aplicația implementează un sistem de tip Role-Based Access Control, adaptând interfața dinamic:

### 🛠️ 1. Administrator
* **Gestiune Completă (CRUD):** Creare, citire, actualizare și ștergere pentru fondul de carte.
* **Gestiune Conturi:** Panou dedicat pentru adăugarea și ștergerea utilizatorilor din sistem, cu protecție împotriva ștergerii ultimului administrator.
* **Statistici și Grafice:** Generare de rapoarte vizuale (Chart-uri) privind numărul de exemplare disponibile per autor.
* **Export Date:** Salvarea bazei de date în format `CSV`.
* **Live Search:** Căutare instantanee după titlu sau autor, cu filtrare în timp real (`DataView`).

### 📖 2. Editor (Bibliotecar)
* Poate adăuga titluri noi și actualiza stocurile.
* **Smart Insert:** La adăugarea unei cărți, sistemul verifică existența autorului. Dacă nu există, îl adaugă automat în fundal (Insert-If-Not-Exists).
* Acces la Live Search și Export CSV.
* *Restricții:* Nu poate șterge cărți definitiv și nu are acces la panoul utilizatorilor.

### 🎓 3. Cititor
* Acces restricționat complet (Read-Only). Interfața ascunde automat formularele și butoanele de manipulare a datelor.
* Poate căuta instant volumele dorite (Live Search) și poate exporta lista (CSV).

---

## 🗄️ Arhitectura Bazei de Date (MySQL)

Baza de date este relațională și optimizată, fiind compusă din 3 entități principale:
1. **`carti`** (id_carte, titlu, an_publicare, gen, exemplare, ISBN, id_autor)
2. **`autori`** (id_autor, nume, prenume) - *Relație 1-la-N cu tabelul cărți.*
3. **`utilizatori`** (id_utilizator, username, parola, rol)

Conexiunea este securizată folosind **interogări parametrizate** (`cmd.Parameters.AddWithValue`) pentru a preveni atacurile de tip SQL Injection.

---

## 💻 Tehnologii și Librării Utilizate
* **Limbaj:** C# (Programare Orientată pe Obiecte)
* **UI:** Windows Forms (WinForms - programatic)
* **Bază de date:** MySQL (accesat via librăria `MySql.Data`)
* **Export Date:** `System.IO` (`StreamWriter`) pentru manipulare File I/O.
* **Grafice:** `System.Windows.Forms.DataVisualization.Charting`

---

## 🚀 Cum să rulezi proiectul local

1. Clonează acest repository pe mașina ta:
   ```bash
   git clone [https://github.com/username-ul-tau/numele-repo-ului.git](https://github.com/username-ul-tau/numele-repo-ului.git)
