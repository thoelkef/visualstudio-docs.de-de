---
title: 'Workflow-Designer - Vorgehensweise: erstellen eine Aktivitätsdesignerbibliothek'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: 5b62e092-63b3-462d-9d77-fb112482f45d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d05ddb48e88627f4b7ab4112c164b5129ddba910
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31974590"
---
# <a name="how-to-create-an-activity-designer-library"></a>Vorgehensweise: Erstellen einer Aktivitätsdesignerbibliothek
Mit benutzerdefinierten Aktivitätsdesignern können Sie für eine benutzerdefinierte Aktivität oder eine Standardaktivität eine Benutzeroberfläche erstellen. Sie steuern die Komplexität der Benutzeroberfläche und sind in der Lage, mehrere Aktivitätsdesigner für eine Aktivität zu erstellen. Dieses Szenario ermöglicht es Ihnen, Designer zu erstellen, die auf unterschiedliche Zielgruppen zugeschnitten sind.

## <a name="to-create-an-activity-designer-library"></a>So erstellen Sie eine Aktivitätsdesignerbibliothek

1.  Starten Sie Visual Studio 2010.

2.  Auf der **Datei** Sie im Menü **neu**, und wählen Sie dann **Projekt** So öffnen die **neues Projekt** (Dialogfeld).

3.  In der **Projekttypen** klicken Sie im Bereich **Workflow** entweder aus der **Visual C#-** oder **Visual Basic** Gruppierungen je nach Ihrer bevorzugten Sprache.

4.  In der **Vorlagen** klicken Sie im Bereich **Aktivitätsdesignerbibliothek**.

5.  In der **Namen** Geben Sie einen beschreibenden Namen für das Projekt in der es einfach identifizieren zu können.

6.  In der **Speicherort** Geben Sie das Verzeichnis, in dem Sie das Projekt gespeichert werden soll, oder klicken möchten **Durchsuchen** navigieren.

7.  In der **Lösung** Feld, geben Sie einen beschreibenden Namen für die Projektmappe, und klicken Sie auf **OK**.

    > [!NOTE]
    > Wenn Sie einer vorhandenen Projektmappe eine workflowkonsolenanwendung hinzufügen möchten, öffnen Sie die Projektmappe in Visual Studio 2010, mit der rechten Maustaste auf die Projektmappe in **Projektmappen-Explorer**, und wählen Sie **hinzufügen**, und klicken Sie dann **Neues Projekt** So öffnen die **neues Projekt** (Dialogfeld). Fahren Sie wie oben in dieser Prozedur beschrieben fort.

8.  Die Projektvorlage erstellt eine Aktivitätsdesignerdefinition in XAML und die Code-Behind-Implementierungsdatei im Quellcode. Windows Workflow-Designer wird geöffnet und zeigt den Canvas für den Aktivitätsdesigner.

9. Ziehen Sie Windows Presentation Foundation (WPF)-Steuerelemente aus der **Toolbox** auf die Entwurfsoberfläche, um sie im benutzerdefinierten Aktivitätsdesigner zu verwenden.  Ein Beispiel zum Implementieren eines benutzerdefinierten Aktivitätsdesigners, finden Sie unter [Vorgehensweise: Erstellen eines benutzerdefinierten Aktivitätsdesigners](/dotnet/framework/windows-workflow-foundation/how-to-create-a-custom-activity-designer).

    > [!WARNING]
    > Benutzerdefinierte Aktivitätsdesigner können für benutzerdefinierte Aktivitäten sowie für das standardmäßige .NET Framework 4activities verwendet werden.

## <a name="see-also"></a>Siehe auch

- [Erstellen eines Workflowprojekts](../workflow-designer/creating-a-workflow-project.md)