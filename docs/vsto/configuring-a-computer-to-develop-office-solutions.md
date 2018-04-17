---
title: Konfigurieren eines Computers zum Entwickeln von Office-Projektmappen | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, installing tools
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 59c00639ce839962c06cacf3c036a5cd8f74b508
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="configuring-a-computer-to-develop-office-solutions"></a>Konfigurieren eines Computers zum Entwickeln von Office-Lösungen

Installieren Sie eine unterstützte Version von Visual Studio, .NET Framework und Microsoft Office, um VSTO-Add-Ins und Anpassungen für Microsoft Office zu erstellen.

|Software|Unterstützte Versionen|
|--------------|------------------------|
|Visual Studio 2017| Eine beliebige Edition mit der **Office/SharePoint-Entwicklung** arbeitsauslastung.|
|.NET Framework|– Die .NET Framework 4 oder höher.|
|Microsoft Office|<ul><li>Eine Suite-Edition von Office, einschließlich Office Professional Plus für Office 365</li><li>Eine der folgenden eigenständigen Anwendungen:<br /><br /> <ul><li>Excel</li><li>InfoPath (nur Office 2013 und Office 2010)</li><li>Outlook</li><li>PowerPoint</li><li>Projekt</li><li>Visio</li><li>Word</li></ul></li></ul><br /> Visual Basic for Applications (VBA) muss als Teil von Office installiert sein. **Wichtig:** Klick-und-Los-Versionen von Office 2010-Anwendungen werden nicht unterstützt.|

Ausführliche Installationsschritte finden Sie unter [Vorgehensweise: Konfigurieren eines Computers zum Entwickeln von Office-Projektmappen](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md).

## <a name="if-project-templates-dont-appear-or-they-dont-work-in-visual-studio"></a>Wenn Projektvorlagen nicht angezeigt werden, oder sie nicht in Visual Studio funktionieren

Wenn Sie eine unterstützte Version von Visual Studio, .NET Framework und Microsoft Office installieren, aber die Office-Projektvorlagen, entweder nicht, in der Visual Studio angezeigt **neues Projekt** (Dialogfeld), oder Sie eine Fehlermeldung erhalten, wenn Sie versuchen, verwenden Überprüfen Sie Folgendes:

- Stellen Sie sicher, dass die Microsoft Office Developer Tools auf Ihrem Computer installiert sind.

     Office Developer Tools sind eine optionale Komponente von Visual Studio, doch sie werden in der Regel automatisch mit Visual Studio installiert. Wenn Sie die Visual Studio-Installation anpassen, indem Sie die zu installierenden Funktionen auswählen, legen Sie beim Setup zum Installieren der Tools **Microsoft Office Developer Tools** fest.

     Um sicherzustellen, dass diese Tools installiert sind, starten Sie Visual Studio-Setupprogramm, und wählen Sie die **ändern** Schaltfläche. Aktivieren Sie das Kontrollkästchen **Microsoft Office Developer Tools** , und wählen Sie dann die Schaltfläche **Aktualisieren** aus.

- Stellen Sie sicher, dass Sie keine Version von Office ausführen, die mittels Klick-und-Los bereitgestellt wurde. Weitere Informationen finden Sie unter [Gewusst wie: Überprüfen, ob Outlook auf einem Computer eine Klick-und-Los-Anwendung ist](http://msdn.microsoft.com/library/office/ff864733(v=office.14).aspx).

- Stellen Sie sicher, dass Sie nur eine Version von Microsoft Office ausführen.

Wenn Sie weiterhin Probleme haben, finden Sie zusätzliche Informationen unter [Additional Support for Errors in Office Solutions](../vsto/additional-support-for-errors-in-office-solutions.md).

## <a name="see-also"></a>Siehe auch

[Erste Schritte &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)  
[Vorgehensweise: Konfigurieren eines Computers zum Entwickeln von Office-Projektmappen](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)  
[Vorgehensweise: Installieren der verteilbaren Visual Studio-Tools für Office Runtime](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)  
[Vorgehensweise: Installieren von primären Interopassemblys für Office](../vsto/how-to-install-office-primary-interop-assemblies.md)  
[Verfügbare Funktionen nach Office-Anwendung und Projekttyp](../vsto/features-available-by-office-application-and-project-type.md)
