---
title: Konfigurieren eines Computers zum Entwickeln von Office-Projektmappen
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
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: a0e6f44b923bf515977c07bbfec69b9c8e58593c
ms.sourcegitcommit: a715de2ba8c703f37aa2102567b1aa2c0f05a117
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2018
ms.locfileid: "53441417"
---
# <a name="configure-a-computer-to-develop-office-solutions"></a>Konfigurieren eines Computers zum Entwickeln von Office-Projektmappen

Installieren Sie eine unterstützte Version von Visual Studio, .NET Framework und Microsoft Office, um VSTO-Add-Ins und Anpassungen für Microsoft Office zu erstellen.

|Software|Unterstützte Versionen|
|--------------|------------------------|
|Visual Studio 2017| Eine beliebige Edition, mit der **Office/SharePoint-Entwicklung** arbeitsauslastung.|
|.NET Framework|– Die .NET Framework 4 oder höher.|
|Microsoft Office|<ul><li>Eine Suite-Edition von Office, einschließlich Office Professional Plus für Office 365</li><li>Eine der folgenden eigenständigen Anwendungen:<br /><br /> <ul><li>Excel</li><li>InfoPath (nur Office 2013 und Office 2010)</li><li>Outlook</li><li>PowerPoint</li><li>Projekt</li><li>Visio</li><li>Word</li></ul></li></ul><br /> Visual Basic for Applications (VBA) muss als Teil von Office installiert sein. **Wichtig:** Klick-und-Los-Versionen von Office 2010-Anwendungen werden nicht unterstützt.|

Ausführliche Installationsschritte finden Sie unter [Vorgehensweise: Konfigurieren ein Computers zum Entwickeln von Office-Projektmappen](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md).

## <a name="if-project-templates-dont-appear-or-they-dont-work-in-visual-studio"></a>Wenn Projektvorlagen nicht angezeigt wird oder nicht in Visual Studio funktionieren

Wenn Sie eine unterstützte Version von Visual Studio, die .NET Framework und Microsoft Office installieren, aber die Office-Projektvorlagen nicht angezeigt in der Visual Studio werden **neues Projekt** (Dialogfeld), oder Sie erhalten einen Fehler auf, wenn Sie versuchen, einen verwenden Überprüfen Sie Folgendes:

- Stellen Sie sicher, dass die Microsoft Office Developer Tools auf Ihrem Computer installiert sind.

     Office Developer Tools sind eine optionale Komponente von Visual Studio, aber sie werden automatisch zusammen mit Visual Studio installiert. Wenn Sie die Visual Studio-Installation anpassen, indem Sie die zu installierenden Funktionen auswählen, legen Sie beim Setup zum Installieren der Tools **Microsoft Office Developer Tools** fest.

     Um sicherzustellen, dass diese Tools installiert sind, starten Sie das Visual Studio-Setup-Programm, und wählen die **ändern** Schaltfläche. Aktivieren Sie das Kontrollkästchen **Microsoft Office Developer Tools** , und wählen Sie dann die Schaltfläche **Aktualisieren** aus.

- Stellen Sie sicher, dass Sie eine Version von Office nicht ausführen, die mittels Klick-und-Los bereitgestellt wurde. Weitere Informationen finden Sie unter [How to: Überprüfen Sie, ob Outlook auf einem Computer eine Klick-und-Los-Anwendung ist](/previous-versions/office/developer/office-2010/ff864733(v=office.14)).

- Stellen Sie sicher, dass Sie nur eine Version von Microsoft Office ausführen.

Wenn Sie Probleme auftreten weiterhin, finden Sie unter [zusätzliche Unterstützung für Fehler in Office-Projektmappen](../vsto/additional-support-for-errors-in-office-solutions.md).

## <a name="see-also"></a>Siehe auch

[Erste Schritte &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)  
[Vorgehensweise: Konfigurieren eines Computers zum Entwickeln von Office-Projektmappen](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)  
[Vorgehensweise: Installieren der Visual Studio-Tools für Office-Laufzeit](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)  
[Vorgehensweise: Installieren von primären Interopassemblys für Office](../vsto/how-to-install-office-primary-interop-assemblies.md)  
[Verfügbare Funktionen nach Office-Anwendung und Projekt geben.](../vsto/features-available-by-office-application-and-project-type.md)
