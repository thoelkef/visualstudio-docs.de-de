---
title: Commit-Prozess interne Bearbeitung von Daten gebundenen Steuerelementen vor dem Speichern von Daten | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- committing edited records
- data-bound controls, in-process edits
- DataBinding class, committing edited records
- hierarchical update, committing edited records
- BindingSource class, committing edited records
- EndEdit method
ms.assetid: 61af4798-eef7-468c-b229-5e1497febb2f
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3867b91a8b417b5670514b66aaf93fdab4e9618c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662451"
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>Ausführen eines Commits für aktuelle Bearbeitungen von datengebundenen Steuerelementen vor dem Speichern von Daten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Beim Bearbeiten von Werten in Daten gebundenen Steuerelementen müssen Benutzer aus dem aktuellen Datensatz navigieren, um den aktualisierten Wert auf die zugrunde liegende Datenquelle zu übertragen, an die das Steuerelement gebunden ist. Wenn Sie Elemente aus dem [Datenquellen Fenster](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) auf ein Formular ziehen, generiert das erste Element, das Sie ablegen, Code im Click-Ereignis der Schaltfläche "Save" ( **Speichern** ) der <xref:System.Windows.Forms.BindingNavigator>. Mit diesem Code wird die <xref:System.Windows.Forms.BindingSource.EndEdit%2A>-Methode des <xref:System.Windows.Forms.BindingSource> aufgerufen. Daher wird der <xref:System.Windows.Forms.BindingSource.EndEdit%2A>-Methode nur für den ersten <xref:System.Windows.Forms.BindingSource> generiert, der dem Formular hinzugefügt wird.

 Der Aufruf <xref:System.Windows.Forms.BindingSource.EndEdit%2A> führt ein Commit aller Änderungen durch, die in irgendeinem datengebundenen Steuerelement ablaufen, das derzeit bearbeitet wird. Wenn also ein datengebundenes Steuerelement den Fokus noch besitzt und Sie auf **Speichern** klicken, werden alle ausstehenden Bearbeitungen in diesem Steuerelement committet, bevor der eigentliche Speichervorgang durchgeführt wird (die `TableAdapterManager.UpdateAll`-Methode).

 Sie können Ihre Anwendung so konfigurieren, dass Änderungen automatisch committet werden, auch wenn ein Benutzer versucht, Daten zu speichern, ohne die Änderungen im Rahmen des Speicher Vorgangs zu übernehmen.

> [!NOTE]
> Der Designer fügt den `BindingSource.EndEdit` Code nur für das erste Element hinzu, das auf einem Formular abgelegt wurde. Daher müssen Sie eine Codezeile hinzufügen, um die <xref:System.Windows.Forms.BindingSource.EndEdit%2A>-Methode für jede <xref:System.Windows.Forms.BindingSource> im Formular aufzurufen. Sie können manuell eine Codezeile hinzufügen, um die <xref:System.Windows.Forms.BindingSource.EndEdit%2A>-Methode für jede <xref:System.Windows.Forms.BindingSource> aufzurufen. Alternativ können Sie dem Formular die `EndEditOnAllBindingSources`-Methode hinzufügen und diese vor dem Durchführen einer Speicherung anrufen.

 Im folgenden Code wird eine [LINQ (Language-Integrated Query)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) -Abfrage verwendet, um alle <xref:System.Windows.Forms.BindingSource> Komponenten zu durchlaufen und die <xref:System.Windows.Forms.BindingSource.EndEdit%2A>-Methode für jede <xref:System.Windows.Forms.BindingSource> in einem Formular aufzurufen.

## <a name="to-call-endedit-for-all-bindingsource-components-on-a-form"></a>So wenden Sie EndEdit für alle BindingSource-Komponenten in einem Formular an

1. Fügen Sie dem Formular den folgenden Code hinzu, der die <xref:System.Windows.Forms.BindingSource> Komponenten enthält.

     [!code-csharp[VSProDataOrcasEndEditOnAll#1](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs#1)]
     [!code-vb[VSProDataOrcasEndEditOnAll#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb#1)]

2. Fügen Sie die folgende Codezeile direkt vor den Aufrufen ein, um die Daten des Formulars zu speichern (die `TableAdapterManager.UpdateAll()`-Methode):

     [!code-csharp[VSProDataOrcasEndEditOnAll#2](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs#2)]
     [!code-vb[VSProDataOrcasEndEditOnAll#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb#2)]

## <a name="see-also"></a>Siehe auch
 [Binden von Windows Forms Steuerelementen an Daten in der hierarchischen Visualisierung von Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) [Hierarchical update](../data-tools/hierarchical-update.md)
