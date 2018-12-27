---
title: Aktivieren des Zugriffs auf VBA erstellen oder Öffnen ein Visual Studio-Tools für die Microsoft Office System-Projekt
decsprition: You must explicitly enable access to the Office VBA project system before you can create or open a Visual Studio Tools for Office system project
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- vst.project.vbawrongversion
- VST.Project.VBASecurityGenericError
- VST.Project.VBASecurityPermissions
- VST.SelectDocWizard.MissingCOM
- VST.Project.VBASecurityNotSet
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1b1a7be701c9bec45011980ced63051150579ca7
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2018
ms.locfileid: "53647569"
---
# <a name="enable-access-to-vba-to-create-or-open-a-visual-studio-tools-for-the-microsoft-office-system-project"></a>Aktivieren des Zugriffs auf VBA erstellen oder Öffnen ein Visual Studio-Tools für die Microsoft Office System-Projekt

Sie müssen Zugriff auf das Visual Basic für Applikationen (VBA)-Projektsystem in Microsoft Office explizit aktivieren, bevor Sie erstellen oder ein Visual Studio-Tools für die Microsoft Office System-Projekt öffnen können.

 Microsoft Office-Projekte erfordern Zugriff auf das Visual Basic for Applications (VBA)-Projektsystem in Microsoft Office Word und Microsoft Office Excel, obwohl diese Projekte nicht Visual Basic für Applikationen verwenden. Unterstützung der Steuerelemente in Visual Basic- und C#-Projekten zur Entwurfszeit ist vom Visual Basic for Applications-Projektsystem abhängig.

 Einige Microsoft Office-Makroviren versuchen das Visual Basic for Applications-Projektsystem als Mittel zur Selbstweitergabe zu automatisieren. Um den Zugriff auf das Visual Basic for Applications-Projektsystem zu aktivieren, entfernen Sie eine Schutzvorrichtung, mit der die Verbreitung von Makroviren verhindert werden kann. Die normale Makrosicherheit wird weiterhin aufrecht erhalten, sodass die Makrosicherheitsebene und die Liste der vertrauenswürdigen Herausgeber, die Sie für Ihre Office-Anwendungen verwalten, bestimmen, ob ein Makro auf Ihrem Computer ausgeführt wird.

> [!NOTE]
> Dies gilt nur für den Entwicklungscomputer. Wenn diese Option aktiviert, die zum Ausführen von Office-Projektmappen erforderlich Endbenutzercomputern nicht.

 Sie sollten beachten, dass die Deaktivierung des Zugriffs auf das Visual Basic for Applications-Projektsystem Sie nicht allein vor Viren schützt. Dadurch wird lediglich die Verbreitung einiger Viren auf andere Dokumente verhindert, wenn Ihr Computer mit einem Makrovirus infiziert werden sollte. Diese Option ist standardmäßig als zusätzliche Schutzstufe für Ihren Computer deaktiviert; die Aktivierung macht Ihren Computer nicht anfälliger für Viren, wenn Sie die Best Practices hinsichtlich der Sicherheit befolgen.

 Der beste Schutz für Office-Makroviren besteht im Ausführen von Office mit der hohen oder sehr hohen Sicherheitsstufe, nur Makros von vertrauen, bekannte Quellen überprüft und mit Sicherheitspatches und Virenscannern auf dem Laufenden bleiben.

 Weitere Informationen zum Schutz Ihres PCs vor Viren und sonstigem bösartigen Code finden Sie unter [ http://www.microsoft.com/protect ](http://www.microsoft.com/protect).

 Sie können aktivieren oder deaktivieren Sie die Option **Zugriff auf Visual Basic-Projekt vertrauen** manuell.

 Sie können die Office-Installation reparieren, wenn VBA- oder COM-Fehler angezeigt werden.

## <a name="to-enable-or-disable-access-to-visual-basic-projects"></a>So aktivieren oder deaktivieren den Zugriff auf Visual Basic-Projekte

1. Klicken Sie auf die Registerkarte **Datei** .

2. Klicken Sie auf **Optionen**.

3. Klicken Sie auf **Trust Center**, und klicken Sie dann auf **Einstellungen für das Sicherheitscenter**.

4. In der **Trust Center**, klicken Sie auf **Makroeinstellungen**.

5. Aktivieren oder deaktivieren Sie **Zugriff auf das VBA-Projektobjektmodell vertrauen** aktivieren oder deaktivieren den Zugriff auf Visual Basic-Projekte.

6. Klicken Sie auf **OK**.

### <a name="to-enable-or-disable-access-to-visual-basic-projects-with-the-2007-microsoft-office-system"></a>So aktivieren oder deaktivieren den Zugriff auf Visual Basic-Projekte mit 2007 Microsoft Office system

1. Auf der **Tools** Menü in Word oder Excel, zeigen Sie auf **Makro**, und klicken Sie dann auf **Sicherheit**.

2. In der **Sicherheit** Dialogfeld klicken Sie auf die **vertrauenswürdige Herausgeber** Registerkarte.

3. Wählen Sie zum Aktivieren oder deaktivieren Sie die Option **Zugriff auf Visual Basic-Projekt vertrauen**.

4. Klicken Sie auf **OK**.

## <a name="to-set-your-office-macro-security-level"></a>So legen Sie die Office-Makrosicherheitsstufe fest

1. Klicken Sie auf die Registerkarte **Datei** .

2. Klicken Sie auf **Optionen**.

3. Klicken Sie auf **Trust Center**, und klicken Sie dann auf **Einstellungen für das Sicherheitscenter**.

4. In der **Trust Center**, klicken Sie auf **Makroeinstellungen**.

5. In der **Makroeinstellungen** wählen die gewünschte Einstellung.

6. Klicken Sie auf **OK**.

### <a name="to-set-your-office-macro-security-level-with-the-2007-microsoft-office-system"></a>Mit 2007 Microsoft Office System Ihre Office-Makrosicherheitsstufe fest

1. Auf der **Tools** Menü in Word oder Excel, zeigen Sie auf **Makro**, und klicken Sie dann auf **Sicherheit**.

2. Auf der **Sicherheitsstufe** Registerkarte, wählen Sie die gewünschte Einstellung.

    Die **Sicherheitsstufe** Registerkarte enthält Details zu jeder Stufe. Weitere Informationen finden Sie im Thema zu Makrosicherheitsstufen in der Office-Hilfe.

### <a name="to-install-vba-with-the-2007-microsoft-office-system"></a>So installieren Sie VBA mit dem Microsoft Office 2007-System

1. Führen Sie in der Systemsteuerung **Software** oder **Programme und Funktionen**.

2. Wählen Sie die Niederlassung in die **momentan installierte Programme** Liste.

3. Klicken Sie auf **Änderung**.

4. Wählen Sie **hinzufügen oder Entfernen von Features**, und klicken Sie dann auf **Weiter**.

5. Wählen Sie **auswählen, die erweiterte Anpassung von Anwendungen**, und klicken Sie dann auf **Weiter**.

6. Erweitern Sie **gemeinsam genutzte Office-Features** in die **wählen Sie die Optionen für Anwendungen und Tools Update** Liste.

7. Öffnen Sie das Dropdownmenü neben **Visual Basic für Applikationen**, und klicken Sie dann auf **vom Arbeitsplatz starten**.

8. Klicken Sie auf **Weiter**.

9. Klicken Sie auf **Schließen**.

## <a name="to-repair-your-installation-of-office"></a>So reparieren Sie Ihre Office-Installation

1. Führen Sie in der Systemsteuerung **Software** oder **Programme und Funktionen**.

2. Wählen Sie Ihre Version von Office in der **momentan installierte Programme** Liste.

3. Klicken Sie auf **Änderung**.

4. Wählen Sie **neu installieren oder reparieren**, und klicken Sie dann auf **Weiter**.

5. Wählen Sie **erkennen und Reparieren von Fehlern in Office-Installation**, und klicken Sie dann auf **installieren**.

## <a name="see-also"></a>Siehe auch

 [Sichern von Office-Projektmappen](../vsto/securing-office-solutions.md)