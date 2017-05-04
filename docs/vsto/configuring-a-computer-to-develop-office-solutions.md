---
title: "Konfigurieren eines Computers zum Entwickeln von Office-L&#246;sungen | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Office-Entwicklung in Visual Studio, Installieren von Tools"
ms.assetid: 0b481186-fd31-43bf-aa4a-591f94309555
caps.latest.revision: 97
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 96
---
# Konfigurieren eines Computers zum Entwickeln von Office-L&#246;sungen
  Installieren Sie eine unterstützte Version von Visual Studio, .NET Framework und Microsoft Office, um VSTO\-Add\-Ins und Anpassungen für Microsoft Office zu erstellen.  
  
|Software|Unterstützte Versionen|  
|--------------|----------------------------|  
|Visual Studio|-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)]<br />-   [!INCLUDE[vsPreShort](../vsto/includes/vspreshort-md.md)]<br />-   [!INCLUDE[vsUltShort](../vsto/includes/vsultshort-md.md)] **Important:**  Sie müssen beim Einrichten das Kontrollkästchen "Microsoft Office Developer Tools" auswählen.|  
|.NET Framework|-   .NET Framework 4 oder höher|  
|Microsoft Office|<ul><li>Eine Suite\-Edition von Office, einschließlich Office Professional Plus für Office 365</li><li>Eine der folgenden eigenständigen Anwendungen:<br /><br /> <ul><li>Excel</li><li>InfoPath \(nur Office 2013 und Office 2010\)</li><li>Outlook</li><li>PowerPoint</li><li>Projekt</li><li>Visio</li><li>Word</li></ul></li></ul><br /> Visual Basic for Applications \(VBA\) muss als Teil von Office installiert sein. **Important:**  Klick\-und\-Los\-Versionen von Office 2010\-Anwendungen werden nicht unterstützt.|  
  
 Ausführliche Installationsschritte finden Sie unter [Gewusst wie: Konfigurieren eines Computers zum Entwickeln von Office-Projektmappen](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md).  
  
## Wenn Projektvorlagen nicht angezeigt werden oder sie nicht in Visual Studio funktionieren  
 Wenn Sie eine unterstützte Version von Visual Studio, dem .NET Framework und Microsoft Office installieren, aber die Office\-Projektvorlagen nicht im Visual Studio\-Dialogfeld **Neues Projekt** angezeigt werden oder Sie beim Versuch eine zu verwenden eine Fehlermeldung erhalten, prüfen Sie Folgendes:  
  
-   Stellen Sie sicher, dass die Microsoft Office Developer Tools auf Ihrem Computer installiert sind.  
  
     Office Developer Tools sind eine optionale Komponente von Visual Studio, doch sie werden in der Regel automatisch mit Visual Studio installiert. Wenn Sie die Visual Studio\-Installation anpassen, indem Sie die zu installierenden Funktionen auswählen, legen Sie beim Setup zum Installieren der Tools **Microsoft Office Developer Tools** fest.  
  
     Starten Sie das Visual Studio\-Setupprogramm, und wählen Sie die Schaltfläche **Ändern**, um sicherzustellen, dass diese Tools installiert werden. Aktivieren Sie das Kontrollkästchen **Microsoft Office Developer Tools**, und wählen Sie dann die Schaltfläche **Aktualisieren** aus.  
  
-   Stellen Sie sicher, dass Sie keine Version von Office ausführen, die mittels Klick\-und\-Los bereitgestellt wurde. Weitere Informationen finden Sie unter [Gewusst wie: Überprüfen, ob Outlook auf einem Computer eine Klick\-und\-Los\-Anwendung ist](http://msdn.microsoft.com/library/office/ff864733(v=office.14).aspx).  
  
-   Stellen Sie sicher, dass Sie nur eine Version von Microsoft Office ausführen.  
  
 Wenn Sie weiterhin Probleme haben, finden Sie zusätzliche Informationen unter [Zusätzliche Unterstützung für Fehler in Office-Projektmappen](../vsto/additional-support-for-errors-in-office-solutions.md).  
  
## Siehe auch  
 [Erste Schritte &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Gewusst wie: Konfigurieren eines Computers zum Entwickeln von Office-Projektmappen](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)   
 [Gewusst wie: Installieren der verteilbaren Visual Studio Tools for Office Runtime](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)   
 [Gewusst wie: Installieren von primären Interopassemblys für Office](../vsto/how-to-install-office-primary-interop-assemblies.md)   
 [Verfügbare Funktionen nach Office-Anwendung und Projekttyp](../vsto/features-available-by-office-application-and-project-type.md)  
  
  