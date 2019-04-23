---
title: Commit in Bearbeitungen von datengebundenen Steuerelementen vor dem Speichern von Daten | Microsoft-Dokumentation
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 813e49ab316f1fe74daa7a797dd6e16a878667d1
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2019
ms.locfileid: "59664582"
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>Ausführen eines Commits für aktuelle Bearbeitungen von datengebundenen Steuerelementen vor dem Speichern von Daten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Beim Bearbeiten der Werte in datengebundenen Steuerelementen müssen Benutzer navigieren, aus der aktuellen Datensatz aus, um den aktualisierten Wert an der zugrunde liegenden Datenquelle zu committen, das das Steuerelement gebunden ist. Beim Ziehen von Elementen aus der [Fensters "Datenquellen"](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) auf ein Formular, das erste Element, das Sie löschen generiert den Code in die **speichern** click-Ereignis von der <xref:System.Windows.Forms.BindingNavigator>. Dieser Code Ruft die <xref:System.Windows.Forms.BindingSource.EndEdit%2A> Methode der <xref:System.Windows.Forms.BindingSource>. Aus diesem Grund wird der Aufruf von der <xref:System.Windows.Forms.BindingSource.EndEdit%2A> Methode wird nur für die erste generiert <xref:System.Windows.Forms.BindingSource> zum Formular hinzugefügt wird.  
  
 Der Aufruf <xref:System.Windows.Forms.BindingSource.EndEdit%2A> führt ein Commit aller Änderungen durch, die in irgendeinem datengebundenen Steuerelement ablaufen, das derzeit bearbeitet wird. Wenn also ein datengebundenes Steuerelement den Fokus noch besitzt und Sie auf **Speichern** klicken, werden alle ausstehenden Bearbeitungen in diesem Steuerelement committet, bevor der eigentliche Speichervorgang durchgeführt wird (die `TableAdapterManager.UpdateAll`-Methode).  
  
 Sie können Ihre Anwendung automatisch, Commits konfigurieren, selbst wenn ein Benutzer versucht, Daten zu speichern, ohne Commit für Änderungen, als Teil des Speichervorgangs Prozess.  
  
> [!NOTE]
>  Der Designer fügt die `BindingSource.EndEdit` Code nur für das erste Element auf einem Formular abgelegt. Aus diesem Grund müssen Sie eine einzige Zeile Code aufrufen, Hinzufügen der <xref:System.Windows.Forms.BindingSource.EndEdit%2A> Methode für die einzelnen <xref:System.Windows.Forms.BindingSource> auf dem Formular. Sie können manuell hinzufügen, eine einzige Zeile Code zum Aufrufen der <xref:System.Windows.Forms.BindingSource.EndEdit%2A> Methode für die einzelnen <xref:System.Windows.Forms.BindingSource>. Sie können auch hinzufügen, die `EndEditOnAllBindingSources` Methode, um das Formular und nennen Sie sie vor dem Ausführen eines Speichervorgangs.  
  
 Der folgende code verwendet ein [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) Abfrage durchlaufen alle <xref:System.Windows.Forms.BindingSource> Komponenten, und rufen die <xref:System.Windows.Forms.BindingSource.EndEdit%2A> Methode für die einzelnen <xref:System.Windows.Forms.BindingSource> in einem Formular.  
  
## <a name="to-call-endedit-for-all-bindingsource-components-on-a-form"></a>EndEdit für alle BindingSource-Komponenten in einem Formular aufgerufen.  
  
1.  Fügen Sie den folgenden Code, um das Formular mit den <xref:System.Windows.Forms.BindingSource> Komponenten.  
  
     [!code-csharp[VSProDataOrcasEndEditOnAll#1](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs#1)]
     [!code-vb[VSProDataOrcasEndEditOnAll#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb#1)]  
  
2.  Fügen Sie die folgende Codezeile unmittelbar vor dem Aufrufen zum Speichern von Daten des Formulars (die `TableAdapterManager.UpdateAll()` Methode):  
  
     [!code-csharp[VSProDataOrcasEndEditOnAll#2](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/CS/Form1.cs#2)]
     [!code-vb[VSProDataOrcasEndEditOnAll#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasEndEditOnAll/VB/Form1.vb#2)]  
  
## <a name="see-also"></a>Siehe auch  
 [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Hierarchische Aktualisierung](../data-tools/hierarchical-update.md)
