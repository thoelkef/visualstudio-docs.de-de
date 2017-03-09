---
title: "Gewusst wie: Speichern und &#214;ffnen von Dateien mit Codierung | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Bidirektionale Sprachenunterstützung, Codierte Dateien"
  - "Dateicodierung, Bidirektionale Sprachen"
  - "Dateien, encoding"
  - "Unicode, Bidirektionale Sprachenunterstützung"
ms.assetid: cb52b732-b395-4ba1-a3ef-104b3942a12a
caps.latest.revision: 8
caps.handback.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Gewusst wie: Speichern und &#214;ffnen von Dateien mit Codierung
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können Dateien mit ausgewählter Zeichencodierung speichern, sodass bidirektionale Sprachen unterstützt werden.  Sie können außerdem auch beim Öffnen einer Datei eine Codierung angeben, sodass Visual Studio die Datei korrekt anzeigt.  
  
### So speichern Sie eine codierte Datei  
  
1.  Klicken Sie im Menü **Datei** auf **Datei speichern unter**, und klicken Sie dann neben der Schaltfläche **Speichern** auf die Dropdownschaltfläche.  
  
     Das Dialogfeld **Erweiterte Speicheroptionen** wird angezeigt.  
  
2.  Wählen Sie unter **Codierung** die gewünschte Codierung für diese Datei aus.  
  
3.  Optional können Sie unter **Zeilenenden** das Format für die Zeichen am Zeilenende auswählen.  
  
     Diese Option ist sehr praktisch, wenn Sie die Datei an Benutzer eines anderen Betriebssystems weitergeben möchten.  
  
     Wenn Sie mit einer Datei arbeiten möchten, von der Sie wissen, wie sie codiert wurde, können Sie in Visual Studio angeben, dass diese Codierung beim Öffnen verwendet werden soll.  Welche Methode Sie verwenden, hängt davon ab, ob die Datei Teil des Projekts ist.  
  
### So öffnen Sie eine codierte Datei, die Teil eines Projekts ist  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf die Datei, und wählen Sie **Öffnen mit** aus.  
  
2.  Wählen Sie im Dialogfeld **Öffnen mit** den Editor aus, mit dem die Datei geöffnet werden soll.  
  
     Viele der Editoren von Visual Studio, z. B. der Formular\-Editor, erkennen die Codierung automatisch und öffnen die Datei dann entsprechend.  Wenn Sie einen Editor verwenden, bei dem Sie eine Codierung auswählen können, wird das Dialogfeld **Codierung** angezeigt.  
  
3.  Wählen Sie in diesem Fall im Dialogfeld **Codierung** die vom Editor zu verwendende Codierung aus.  
  
### So öffnen Sie eine codierte Datei, die nicht Teil eines Projekts ist  
  
1.  Zeigen Sie im Menü **Datei** auf **Öffnen**, wählen Sie **Datei** oder **Datei im Web** aus, und wählen Sie dann die zu öffnende Datei aus.  
  
2.  Klicken Sie neben der Schaltfläche **Öffnen** auf die Dropdownschaltfläche, und klicken Sie auf **Öffnen mit**.  
  
3.  Führen Sie die Schritte 2 und 3 der vorherigen Prozedur aus.  
  
## Siehe auch  
 [Codierung und die Globalisierung von Windows Forms](../Topic/Encoding%20and%20Windows%20Forms%20Globalization.md)   
 [Globalisieren und Lokalisieren von Anwendungen](../ide/globalizing-and-localizing-applications.md)