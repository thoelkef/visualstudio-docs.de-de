---
title: "Schritt 8: Anpassen des Quiz | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# Schritt 8: Anpassen des Quiz
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Im letzten Teil des Lernprogramms untersuchen Sie mehrere Möglichkeiten, das Quiz anzupassen. Damit erweitern Sie Ihre bereits erworbenen Kenntnisse.  Sie können z. B. überlegen, wie das Programm zufällige Divisionsaufgaben erstellt, für die die Antwort nie eine Bruchzahl ist.  Um den Lerneffekt zu erhöhen, können Sie für das `timeLabel`\-Steuerelement eine andere Farbe festlegen und dem Quizteilnehmer einen Hinweis geben.  
  
### So passen Sie das Quiz an  
  
-   Ändern Sie das Steuerelement **timeLabel** in Rot, wenn nur noch fünf Sekunden zur Durchführung des Quiz verbleiben. Legen Sie dazu die Eigenschaft **BackColor** \(`timeLabel.BackColor = Color.Red;`\) für das Steuerelement fest.  Setzen Sie die Farbe zurück, wenn das Quiz vorbei ist.  
  
-   Geben Sie dem Quizteilnehmer einen Hinweis, indem Sie einen Sound wiedergeben, wenn in ein NumericUpDown\-Steuerelement die richtige Antwort eingegeben wird. \(Sie müssen für jedes Steuerelement einen Ereignishandler für das `ValueChanged()`\-Ereignis schreiben, das ausgelöst wird, wenn der Quizteilnehmer den Wert des Steuerelements ändert.\)  
  
### So fahren Sie fort oder überprüfen die Angaben  
  
-   Informationen zum Herunterladen einer vollständige Version des Quiz finden Sie unter [Referentenbeispiel des vollständigen Mathequiz](http://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).  
  
-   Um zum nächsten Lernprogramm zu wechseln, klicken Sie auf [Lernprogramm 3: Erstellen eines Vergleichsspiels](../ide/tutorial-3-create-a-matching-game.md).  
  
-   Um zum vorherigen Schritt des Lernprogramms zurückzukehren, klicken Sie auf [Schritt 7: Hinzufügen von Multiplikations\- und Divisionsaufgaben](../ide/step-7-add-multiplication-and-division-problems.md).