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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 58458b51115834b5b94e858676ee8039d5894c70
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
---
# <a name="configure-a-computer-to-develop-office-solutions"></a>Konfigurieren eines Computers zum Entwickeln von Office-Projektmappen

Installieren Sie eine unterstützte Version von Visual Studio, .NET Framework und Microsoft Office, um VSTO-Add-Ins und Anpassungen für Microsoft Office zu erstellen.

|Software|Unterstützte Versionen|
|--------------|------------------------|
|Visual Studio 2017| Eine beliebige Edition mit der **Office/SharePoint-Entwicklung** arbeitsauslastung.|
|.NET Framework|– Die .NET Framework 4 oder höher.|
|Microsoft Office|<ul><li>Eine Suite-Edition von Office, einschließlich Office Professional Plus für Office 365</li><li>Eine der folgenden eigenständigen Anwendungen:<br /><br /> <ul><li>Excel</li><li>InfoPath (nur Office 2013 und Office 2010)</li><li>Outlook</li><li>PowerPoint</li><li>Projekt</li><li>Visio</li><li>Word</li></ul></li></ul><br /> Visual Basic for Applications (VBA) muss als Teil von Office installiert sein. **Wichtig:** Klick-und-Los-Versionen von Office 2010-Anwendungen werden nicht unterstützt.|

Ausführliche Installationsschritte finden Sie unter [Vorgehensweise: konfigurieren ein Computers zum Entwickeln von Office-Projektmappen](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md).

## <a name="if-project-templates-dont-appear-or-they-dont-work-in-visual-studio"></a>Wenn Projektvorlagen nicht angezeigt werden, oder sie nicht in Visual Studio funktionieren

Wenn Sie eine unterstützte Version von Visual Studio, .NET Framework und Microsoft Office installieren, aber die Office-Projektvorlagen, entweder nicht, in der Visual Studio angezeigt **neues Projekt** (Dialogfeld), oder Sie eine Fehlermeldung erhalten, wenn Sie versuchen, verwenden Überprüfen Sie Folgendes:

- Stellen Sie sicher, dass die Microsoft Office Developer Tools auf Ihrem Computer installiert sind.

     Office Developer Tools sind eine optionale Komponente von Visual Studio, doch sie werden in der Regel automatisch mit Visual Studio installiert. Wenn Sie die Visual Studio-Installation anpassen, indem Sie die zu installierenden Funktionen auswählen, legen Sie beim Setup zum Installieren der Tools **Microsoft Office Developer Tools** fest.

     Um sicherzustellen, dass diese Tools installiert sind, starten Sie Visual Studio-Setupprogramm, und wählen Sie die **ändern** Schaltfläche. Aktivieren Sie das Kontrollkästchen **Microsoft Office Developer Tools** , und wählen Sie dann die Schaltfläche **Aktualisieren** aus.

- Stellen Sie sicher, dass Sie keine Version von Office ausführen, die mittels Klick-und-Los bereitgestellt wurde. Finden Sie unter [Vorgehensweise: Überprüfen Sie, ob Outlook auf einem Computer eine Klick-und-Los-Anwendung ist](http://msdn.microsoft.com/library/office/ff864733(v=office.14).aspx).

- Stellen Sie sicher, dass Sie nur eine Version von Microsoft Office ausführen.

Wenn Sie Probleme auftreten weiterhin, finden Sie unter [zusätzliche Unterstützung für Fehler in Office-Projektmappen](../vsto/additional-support-for-errors-in-office-solutions.md).

## <a name="see-also"></a>Siehe auch

[Erste Schritte &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)  
[Vorgehensweise: konfigurieren ein Computers zum Entwickeln von Office-Projektmappen](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)  
[Vorgehensweise: Installieren der Visual Studio-Tools für Office-Laufzeit](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)  
[Vorgehensweise: Installieren von Office primary Interop-Assemblys](../vsto/how-to-install-office-primary-interop-assemblies.md)  
[Geben Sie verfügbare Funktionen nach Office-Anwendung und Projekt](../vsto/features-available-by-office-application-and-project-type.md)
