---
title: Konfigurieren eines Computers zum Entwickeln von Office-Projektmappen | Microsoft Docs
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: Office development in Visual Studio, installing tools
ms.assetid: 0b481186-fd31-43bf-aa4a-591f94309555
caps.latest.revision: "97"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2d3e0b354375d6116a1bcc0cc2b0d69ecc2f16b5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="configuring-a-computer-to-develop-office-solutions"></a>Konfigurieren eines Computers zum Entwickeln von Office-Lösungen
  Installieren Sie eine unterstützte Version von Visual Studio, .NET Framework und Microsoft Office, um VSTO-Add-Ins und Anpassungen für Microsoft Office zu erstellen.  
  
|Software|Unterstützte Versionen|  
|--------------|------------------------|  
|Visual Studio|-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)]<br />-   [!INCLUDE[vsPreShort](../vsto/includes/vspreshort-md.md)]<br />-   [!INCLUDE[vsUltShort](../vsto/includes/vsultshort-md.md)]**Wichtig:** müssen Sie das Kontrollkästchen für die Microsoft Office Developer Tools während des Setups auswählen.|  
|.NET Framework|– Die .NET Framework 4 oder höher.|  
|Microsoft Office|<ul><li>Eine Suite-Edition von Office, einschließlich Office Professional Plus für Office 365</li><li>Eine der folgenden eigenständigen Anwendungen:<br /><br /> <ul><li>Excel</li><li>InfoPath (nur Office 2013 und Office 2010)</li><li>Outlook</li><li>PowerPoint</li><li>Projekt</li><li>Visio</li><li>Word</li></ul></li></ul><br /> Visual Basic for Applications (VBA) muss als Teil von Office installiert sein. **Wichtig:** Klick-und-Los-Versionen von Office 2010-Anwendungen werden nicht unterstützt.|  
  
 Ausführliche Installationsschritte finden Sie unter [Vorgehensweise: Konfigurieren eines Computers zum Entwickeln von Office-Projektmappen](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md).  
  
## <a name="if-project-templates-dont-appear-or-they-dont-work-in-visual-studio"></a>Wenn Projektvorlagen nicht angezeigt werden, oder sie nicht in Visual Studio funktionieren  
 Wenn Sie eine unterstützte Version von Visual Studio, .NET Framework und Microsoft Office installieren, aber die Office-Projektvorlagen, entweder nicht, in der Visual Studio angezeigt **neues Projekt** (Dialogfeld), oder Sie eine Fehlermeldung erhalten, wenn Sie versuchen, verwenden Überprüfen Sie Folgendes:  
  
-   Stellen Sie sicher, dass die Microsoft Office Developer Tools auf Ihrem Computer installiert sind.  
  
     Office Developer Tools sind eine optionale Komponente von Visual Studio, doch sie werden in der Regel automatisch mit Visual Studio installiert. Wenn Sie die Visual Studio-Installation anpassen, indem Sie die zu installierenden Funktionen auswählen, legen Sie beim Setup zum Installieren der Tools **Microsoft Office Developer Tools** fest.  
  
     Starten Sie das Visual Studio-Setupprogramm, und wählen Sie die Schaltfläche **Ändern** , um sicherzustellen, dass diese Tools installiert werden. Aktivieren Sie das Kontrollkästchen **Microsoft Office Developer Tools** , und wählen Sie dann die Schaltfläche **Aktualisieren** aus.  
  
-   Stellen Sie sicher, dass Sie keine Version von Office ausführen, die mittels Klick-und-Los bereitgestellt wurde. Weitere Informationen finden Sie unter [Gewusst wie: Überprüfen, ob Outlook auf einem Computer eine Klick-und-Los-Anwendung ist](http://msdn.microsoft.com/library/office/ff864733(v=office.14).aspx).  
  
-   Stellen Sie sicher, dass Sie nur eine Version von Microsoft Office ausführen.  
  
 Wenn Sie weiterhin Probleme haben, finden Sie zusätzliche Informationen unter [Additional Support for Errors in Office Solutions](../vsto/additional-support-for-errors-in-office-solutions.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Erste Schritte &#40; Office-Entwicklung in Visual Studio &#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Vorgehensweise: konfigurieren ein Computers zum Entwickeln von Office-Projektmappen](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)   
 [Vorgehensweise: Installieren von Visual Studio-Tools für Office-Laufzeit](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)   
 [Vorgehensweise: Installieren von primären Interopassemblys für Office](../vsto/how-to-install-office-primary-interop-assemblies.md)   
 [Verfügbare Funktionen nach Office-Anwendung und Projekttyp](../vsto/features-available-by-office-application-and-project-type.md)  
  
  