---
title: Barrierefreiheit in Office-Projekten
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, accessibility
- shortcut keys [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], shortcut keys
- accessibility [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a54c9d5322b35092d635edd00e3b200ee67997a9
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60070042"
---
# <a name="accessibility-in-office-projects"></a>Barrierefreiheit in Office-Projekten

Microsoft Visual Studio und Microsoft Office enthalten zahlreiche Funktionen zur Barrierefreiheit, mit denen Sie benutzerdefinierte Lösungen zu erstellen, die Zugriff auf standard-Anforderungen erfüllen. Microsoft veröffentlicht Richtlinien für den Zugriff auf im Web. Weitere Informationen finden Sie unter den [-Website für Barrierefreiheit](http://go.microsoft.com/fwlink/?LinkID=37113).

In den meisten Fällen erfüllen die Office-Projekten in Visual Studio Accessibility Standards oder macht Eigenschaften, die Sie festlegen können, um Ihre Lösungen zugänglich zu machen. Es gibt jedoch einige Features, die Zugriff auf eingeschränkte haben.

[!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="accessibility-at-design-time"></a>Barrierefreiheit zur Entwurfszeit

### <a name="use-shortcut-keys-in-document-level-projects"></a>Verwenden von Tastenkombinationen in Projekten auf Dokumentebene
 Wenn Microsoft Office Word-Dokument oder einer Microsoft Office Excel-Arbeitsmappe in Visual Studio geöffnet ist, empfängt nur eine Anwendung zu einem Zeitpunkt Befehle der Tastenkombination. Standardmäßig erhält das Visual Studio alle Befehle für Tastenkombination, Sie können jedoch Word- oder Excel, die sie empfangen werden, wenn das Dokument den Fokus durch Auswahl besitzt **Dynamisches Tastaturschema** auf die **Tastatureinstellungen** Seite von der **Optionen** Dialogfeld. Weitere Informationen finden Sie unter [Microsoft Office Word-Tastatur, Microsoft Office-Tastatureinstellungen, Dialogfeld Optionen](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md) und [Microsoft Office Excel-Tastatur, Microsoft Office-Tastatureinstellungen, Dialogfeld "Optionen"](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md).

### <a name="display-shortcut-keys-for-the-ribbon-in-document-level-projects"></a>Anzeigen von Tastenkombinationen für die Multifunktionsleiste in Projekten auf Dokumentebene
 Wenn Sie ein Word-Dokument oder eine Excel-Arbeitsmappe in Visual Studio geöffnet ist, drücken Sie können nicht die **Alt** -Taste, um die Tastenkombinationen für die Registerkarten und Steuerelemente auf dem Menüband anzeigen. Um die Tastenkombinationen anzuzeigen, während das Dokument oder die Arbeitsmappe im Designer geöffnet ist, führen Sie die folgenden Schritte aus.

#### <a name="to-view-shortcut-keys-for-ribbon-tabs-and-controls-in-the-designer"></a>Um Tastenkombinationen für die Multifunktionsleiste Registerkarten und Steuerelemente im Designer anzuzeigen.

1. In Visual Studio auf die **Tools** Menü klicken Sie auf **Optionen**.

2. Erweitern Sie die **Büroanwendungen** Knoten, und wählen **Microsoft Office Excel-Tastatur** oder **Microsoft Office Word-Tastatur**je nach Bedarf.

3. Wählen Sie **Dynamisches Tastaturschema**.

     Es wird eine Meldung angezeigt, die besagt, dass Sie Visual Studio für die Änderung wirksam wird neu gestartet werden müssen.

4. Klicken Sie auf **OK**.

5. Starten Sie Visual Studio neu, und öffnen Sie Ihr Projekt.

6. Öffnen Sie den Dokument oder die Arbeitsmappe Designer für das Projekt.

7. Drücken Sie **F6** die Tastenkombinationen für das Menüband angezeigt werden soll.

## <a name="accessibility-at-runtime"></a>Zugriff zur Laufzeit

### <a name="windows-forms-controls-on-office-documents"></a>Windows Forms-Steuerelemente für Office-Dokumente
 Windows Forms-Steuerelemente verfügbar machen Eigenschaften von Bedienungshilfen um Informationen über das Steuerelement an Eingabehilfen, z.B. die Sprachausgabe bereitzustellen. Profitieren Sie von diesen Eigenschaften von Bedienungshilfen, wenn die Steuerelemente in Office-Dokumenten in einer Anpassung auf Dokumentebene befinden. Weitere Informationen finden Sie unter [bieten Informationen über Eingabehilfen für Steuerelemente auf einem Windows Form](/dotnet/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form).

 Es gibt jedoch auch einige Einschränkungen Zugriff zur Laufzeit ein Windows Forms-Steuerelemente auf einem Excel-Arbeitsmappe oder ein Word-Dokument gehostet werden:

- Sie können nicht von einem Steuerelement in eine andere Registerkarte.

- Steuerelemente in einem Dokument sind deaktiviert, wenn Sie die zoomeinstellung des Dokuments in etwas anderes als 100 % ändern.

  Weitere Informationen zu Einschränkungen für Windows Forms-Steuerelemente in Dokumenten finden Sie unter [Einschränkungen von Windows Forms-Steuerelemente für Office-Dokumente](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).

### <a name="actions-panes-and-custom-task-panes"></a>Aktionsbereiche und benutzerdefinierte Aufgabenbereiche
 Wenn ein Bereich "Aktionen" oder einen benutzerdefinierten Aufgabenbereich den Fokus besitzt, greifen Sie auf die Steuerelemente die gleiche Weise, die Sie Steuerelemente auf einer Windows Forms-Anwendung zugreifen würden. Um den Cursor zwischen den Bereich "Aktionen" und dem Dokument zu verschieben, drücken Sie **F6**.

 Weitere Informationen zu Aktionsbereichen und benutzerdefinierten Aufgabenbereichen, finden Sie unter [aktionsbereichsübersicht](../vsto/actions-pane-overview.md) und [von benutzerdefinierten Aufgabenbereichen](../vsto/custom-task-panes.md).

### <a name="display-modes"></a>Anzeigemodi

Visual Studio verfügt über die folgenden Einschränkungen, die im Zusammenhang mit der Anzeigemodi:

- Steuerelemente in einem Word-Dokument oder eine Excel-Arbeitsblatt sind deaktiviert, wenn Sie die zoomeinstellung des Dokuments in etwas anderes als 100 % ändern.

- Die **neues Projekt** Dialogfeld zeigt keine Steuerelemente ordnungsgemäß, wenn ein Benutzer des Computers Eingabehilfen, ändert **Kontrast**.

Sie können die Bildschirmlupe verwenden, um diese Einschränkungen zu umgehen. Bildschirmlupe ist eine Anzeige-Dienstprogramm in Windows, die ein separates Fenster erstellt, in dem einen vergrößerten Teil des Bildschirms angezeigt.

## <a name="see-also"></a>Siehe auch

- [Entwickeln von Office-Projektmappen](../vsto/developing-office-solutions.md)
- [Steuerelemente für Office-Dokumente](../vsto/controls-on-office-documents.md)
- [Barrierefreiheit für Personen mit behinderungen](../ide/reference/accessibility-for-people-with-disabilities.md)
- [Barrierefreiheitsfeatures in Visual Studio](../ide/reference/accessibility-features-of-visual-studio.md)