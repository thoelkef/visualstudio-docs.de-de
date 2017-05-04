---
title: "Sie m&#252;ssen den Zugriff auf das Microsoft&#160;Office&#160;Visual&#160;Basic for Applications-Projektsystem explizit aktivieren, bevor Sie ein Microsoft&#160;Visual&#160;Studio Tools for the Microsoft Office System-Projekt erstellen oder &#246;ffnen k&#246;nnen | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vst.project.vbawrongversion"
  - "VST.Project.VBASecurityGenericError"
  - "VST.Project.VBASecurityPermissions"
  - "VST.SelectDocWizard.MissingCOM"
  - "VST.Project.VBASecurityNotSet"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: 538021e6-1776-453d-9899-d7fca2f1f58f
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# Sie m&#252;ssen den Zugriff auf das Microsoft&#160;Office&#160;Visual&#160;Basic for Applications-Projektsystem explizit aktivieren, bevor Sie ein Microsoft&#160;Visual&#160;Studio Tools for the Microsoft Office System-Projekt erstellen oder &#246;ffnen k&#246;nnen
  Für Office\-Entwicklungsprojekte ist der Zugriff auf das Visual Basic for Applications\-Projektsystem in Microsoft Office Word und Microsoft Office Excel erforderlich, selbst wenn die Projekte nicht Visual Basic for Applications verwenden.  Unterstützung der Steuerelemente in Visual Basic\- und C\#\-Projekten zur Entwurfszeit ist vom Visual Basic for Applications\-Projektsystem abhängig.  
  
 Einige Microsoft Office\-Makroviren versuchen das Visual Basic for Applications\-Projektsystem als Mittel zur Selbstweitergabe zu automatisieren.  Um den Zugriff auf das Visual Basic for Applications\-Projektsystem zu aktivieren, entfernen Sie eine Schutzvorrichtung, mit der die Verbreitung von Makroviren verhindert werden kann.  Die normale Makrosicherheit wird weiterhin aufrecht erhalten, sodass die Makrosicherheitsebene und die Liste der vertrauenswürdigen Herausgeber, die Sie für Ihre Office\-Anwendungen verwalten, bestimmen, ob ein Makro auf Ihrem Computer ausgeführt wird.  
  
> [!NOTE]  
>  Dies gilt nur für den Entwicklungscomputer.  Für Computer von Endbenutzer muss diese Option nicht aktiviert sein, um Office\-Lösungen auszuführen.  
  
 Sie sollten beachten, dass die Deaktivierung des Zugriffs auf das Visual Basic for Applications\-Projektsystem Sie nicht allein vor Viren schützt. Dadurch wird lediglich die Verbreitung einiger Viren auf andere Dokumente verhindert, wenn Ihr Computer mit einem Makrovirus infiziert werden sollte.  Diese Option ist standardmäßig als zusätzliche Schutzstufe für Ihren Computer deaktiviert; die Aktivierung macht Ihren Computer nicht anfälliger für Viren, wenn Sie die Best Practices hinsichtlich der Sicherheit befolgen.  
  
 Der beste Schutz vor Office\-Makroviren besteht im Ausführen von Office mit einer hohen oder sehr hohen Sicherheitsstufe, sodass nur Makros von überprüften, bekannten Quellen vertraut wird, und im Aktualisieren mit Sicherheitspatches und Virenscannern.  
  
 Weitere Informationen zum Schutz Ihres PCs vor Viren und anderem bösartigen Code finden Sie unter [http:\/\/www.microsoft.com\/protect](http://www.microsoft.com/protect).  
  
 Sie können die Option **Zugriff auf Visual Basic\-Projekt vertrauen** manuell aktivieren oder deaktivieren.  
  
 Sie können die Office\-Installation reparieren, wenn VBA\- oder COM\-Fehler angezeigt werden.  
  
### So aktivieren oder deaktivieren Sie den Zugriff auf Visual Basic\-Projekte  
  
1.  Zeigen Sie im Menü **Extras** in Word oder Excel auf **Makro**, und klicken Sie dann auf **Sicherheit**.  
  
2.  Klicken Sie im Dialogfeld **Sicherheit** auf die Registerkarte **Vertrauenswürdige Herausgeber**.  
  
3.  Wählen Sie **Zugriff auf Visual Basic\-Projekt vertrauen** zum Aktivieren aus, oder heben Sie die Auswahl zum Deaktivieren auf.  
  
4.  Klicken Sie auf **OK**.  
  
### So legen Sie die Office\-Makrosicherheitsstufe fest  
  
1.  Zeigen Sie im Menü **Extras** in Word oder Excel auf **Makro**, und klicken Sie dann auf **Sicherheit**.  
  
2.  Wählen Sie auf der Registerkarte **Sicherheitsstufe** die gewünschte Einstellung aus.  
  
     Die Registerkarte **Sicherheitsstufe** enthält Details zu jeder Stufe.  Weitere Informationen finden Sie im Thema zu Makrosicherheitsstufen in der Office\-Hilfe.  
  
### So installieren Sie VBA mit dem Microsoft Office 2007\-System  
  
1.  Führen Sie in der Systemsteuerung **Programme hinzufügen oder entfernen** bzw. **Programme und Funktionen** aus.  
  
2.  Wählen Sie in der Liste **Momentan installierte Programme** die Option "Office" aus.  
  
3.  Klicken Sie auf **Ändern**.  
  
4.  Wählen Sie **Features hinzufügen oder entfernen** aus, und klicken Sie dann auf **Weiter**.  
  
5.  Wählen Sie **Erweiterte Anpassung von Anwendungen** aus, und klicken Sie dann auf **Weiter**.  
  
6.  Erweitern Sie in der Liste **Aktualisierungsoptionen für Anwendungen und Tools auswählen** die Option **Gemeinsam genutzte Office\-Features**.  
  
7.  Öffnen Sie das Dropdown\-Menü neben **Visual Basic for Applications**, und klicken Sie dann auf **Von 'Arbeitsplatz' ausführen**.  
  
8.  Klicken Sie auf **Weiter**.  
  
9. Klicken Sie auf **Schließen**.  
  
### So reparieren Sie Ihre Office\-Installation  
  
1.  Führen Sie in der Systemsteuerung **Programme hinzufügen oder entfernen** bzw. **Programme und Funktionen** aus.  
  
2.  Wählen Sie in der Liste **Momentan installierte Programme** Ihre Office\-Version aus.  
  
3.  Klicken Sie auf **Ändern**.  
  
4.  Wählen Sie **Neu installieren oder reparieren** aus, und klicken Sie dann auf **Weiter**.  
  
5.  Wählen Sie **Fehlerhafte Office\-Installation erkennen und reparieren** aus, und klicken Sie dann auf **Installieren**.  
  
## Siehe auch  
 [Sichern von Office-Projektmappen](../vsto/securing-office-solutions.md)  
  
  