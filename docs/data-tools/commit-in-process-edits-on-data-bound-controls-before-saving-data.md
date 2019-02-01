---
title: Ausführen eines Commits für aktuelle Bearbeitungen von datengebundenen Steuerelementen vor dem Speichern von Daten
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- committing edited records
- data-bound controls, in-process edits
- DataBinding class, committing edited records
- hierarchical update, committing edited records
- BindingSource class, committing edited records
- EndEdit method
ms.assetid: 61af4798-eef7-468c-b229-5e1497febb2f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 936fb3ea1a5faae942c2c0b614a27c0a037c9dd6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55001747"
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>Ausführen eines Commits für aktuelle Bearbeitungen von datengebundenen Steuerelementen vor dem Speichern von Daten

Beim Bearbeiten der Werte in datengebundenen Steuerelementen müssen Benutzer navigieren, aus der aktuellen Datensatz aus, um den aktualisierten Wert an der zugrunde liegenden Datenquelle zu committen, das das Steuerelement gebunden ist. Beim Ziehen von Elementen aus der [Fensters "Datenquellen"](add-new-data-sources.md) auf ein Formular, das erste Element, das Sie löschen generiert den Code in die **speichern** click-Ereignis von der <xref:System.Windows.Forms.BindingNavigator>. Dieser Code Ruft die <xref:System.Windows.Forms.BindingSource.EndEdit%2A> Methode der <xref:System.Windows.Forms.BindingSource>. Aus diesem Grund wird der Aufruf von der <xref:System.Windows.Forms.BindingSource.EndEdit%2A> Methode wird nur für die erste generiert <xref:System.Windows.Forms.BindingSource> zum Formular hinzugefügt wird.

Der Aufruf <xref:System.Windows.Forms.BindingSource.EndEdit%2A> führt ein Commit aller Änderungen durch, die in irgendeinem datengebundenen Steuerelement ablaufen, das derzeit bearbeitet wird. Wenn also ein datengebundenes Steuerelement den Fokus noch besitzt und Sie auf **Speichern** klicken, werden alle ausstehenden Bearbeitungen in diesem Steuerelement committet, bevor der eigentliche Speichervorgang durchgeführt wird (die `TableAdapterManager.UpdateAll`-Methode).

Sie können Ihre Anwendung automatisch, Commits konfigurieren, selbst wenn ein Benutzer versucht, Daten zu speichern, ohne Commit für Änderungen, als Teil des Speichervorgangs Prozess.

> [!NOTE]
> Der Designer fügt die `BindingSource.EndEdit` Code nur für das erste Element auf einem Formular abgelegt. Aus diesem Grund müssen Sie eine einzige Zeile Code aufrufen, Hinzufügen der <xref:System.Windows.Forms.BindingSource.EndEdit%2A> Methode für die einzelnen <xref:System.Windows.Forms.BindingSource> auf dem Formular. Sie können manuell hinzufügen, eine einzige Zeile Code zum Aufrufen der <xref:System.Windows.Forms.BindingSource.EndEdit%2A> Methode für die einzelnen <xref:System.Windows.Forms.BindingSource>. Sie können auch hinzufügen, die `EndEditOnAllBindingSources` Methode, um das Formular und nennen Sie sie vor dem Ausführen eines Speichervorgangs.

Der folgende code verwendet ein [LINQ (Language-Integrated Query)](/dotnet/csharp/linq/) Abfrage durchlaufen alle <xref:System.Windows.Forms.BindingSource> Komponenten, und rufen die <xref:System.Windows.Forms.BindingSource.EndEdit%2A> Methode für die einzelnen <xref:System.Windows.Forms.BindingSource> in einem Formular.

## <a name="to-call-endedit-for-all-bindingsource-components-on-a-form"></a>EndEdit für alle BindingSource-Komponenten in einem Formular aufgerufen.

1.  Fügen Sie den folgenden Code, um das Formular mit den <xref:System.Windows.Forms.BindingSource> Komponenten.

     [!code-csharp[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.vb)]

2.  Fügen Sie die folgende Codezeile unmittelbar vor dem Aufrufen zum Speichern von Daten des Formulars (die `TableAdapterManager.UpdateAll()` Methode):

     [!code-csharp[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.vb)]

## <a name="see-also"></a>Siehe auch

- [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Hierarchische Aktualisierung](../data-tools/hierarchical-update.md)