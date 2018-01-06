---
title: Commit in Bearbeitungen von datengebundenen Steuerelementen vor dem Speichern | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- commiting edited records
- data-bound controls, in-process edits
- DataBinding class, commiting edited records
- hierarchical update, commiting edited records
- BindingSource class, commiting edited records
- EndEdit method
ms.assetid: 61af4798-eef7-468c-b229-5e1497febb2f
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 38d50f1e3da0004869ae66df8e486affa1b68c2d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>Commit in Bearbeitungen von datengebundenen Steuerelementen vor dem Speichern
Wenn Sie Werte in datengebundene Steuerelemente zu bearbeiten, müssen Benutzer navigieren, aus dem aktuellen Datensatz, um den aktualisierten Wert für den zugrunde liegenden Datenquelle zu übernehmen, die das Steuerelement gebunden ist. Beim Ziehen von Elementen aus der [Datenquellenfenster](add-new-data-sources.md) auf ein Formular, das erste Element, das Sie löschen generiert den Code in der **speichern** click-Ereignis von der <xref:System.Windows.Forms.BindingNavigator>. Dieser Code Ruft die <xref:System.Windows.Forms.BindingSource.EndEdit%2A> Methode der <xref:System.Windows.Forms.BindingSource>. Aus diesem Grund wird der Aufruf von der <xref:System.Windows.Forms.BindingSource.EndEdit%2A> -Methode wird nur für die erste generiert <xref:System.Windows.Forms.BindingSource> , die dem Formular hinzugefügt wird.  
  
 Die <xref:System.Windows.Forms.BindingSource.EndEdit%2A> Aufruf führt einen Commit für alle Änderungen, die, in irgendeinem datengebundenen Steuerelement ablaufen, das derzeit bearbeitet wird. Aus diesem Grund, wenn ein datengebundenes Steuerelement noch einen Fokus hat und Sie klicken die **speichern** Schaltfläche alle ausstehenden Bearbeitungen insofern, dass Steuerelement werden vor dem eigentlichen speichern durchgeführt (die `TableAdapterManager.UpdateAll` Methode).  
  
 Sie können Ihre Anwendung beim commit der Änderungen, automatisch konfigurieren, selbst wenn ein Benutzer versucht, Daten zu speichern, ohne dass die Änderungen im Rahmen des Sicherungspunkts Prozess.  
  
> [!NOTE]
>  Der Designer fügt die `BindingSource.EndEdit` Code nur für das erste Element auf einem Formular abgelegte. Aus diesem Grund müssen Sie eine Codezeile zum Aufrufen Hinzufügen der <xref:System.Windows.Forms.BindingSource.EndEdit%2A> Methode für die einzelnen <xref:System.Windows.Forms.BindingSource> auf dem Formular. Sie können manuell hinzufügen, eine Codezeile zum Aufrufen der <xref:System.Windows.Forms.BindingSource.EndEdit%2A> Methode für die einzelnen <xref:System.Windows.Forms.BindingSource>. Sie können auch hinzufügen die `EndEditOnAllBindingSources` Methode, um das Formular, und rufen sie vor dem Ausführen eines Speichervorgangs.  
  
 Der folgende code verwendet eine [LINQ (Language-Integrated Query)](/dotnet/csharp/linq/) Abfrage durchlaufen alle <xref:System.Windows.Forms.BindingSource> Komponenten, und rufen die <xref:System.Windows.Forms.BindingSource.EndEdit%2A> Methode für die einzelnen <xref:System.Windows.Forms.BindingSource> in einem Formular.  
  
## <a name="to-call-endedit-for-all-bindingsource-components-on-a-form"></a>Aufrufen von EndEdit für alle BindingSource-Komponenten auf einem Formular  
  
1.  Fügen Sie den folgenden Code, um das Formular mit dem <xref:System.Windows.Forms.BindingSource> Komponenten.  
  
     [!code-csharp[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#1](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_1.vb)]  
  
2.  Fügen Sie die folgende Codezeile unmittelbar vor allen Aufrufen zum Speichern von Daten des Formulars (die `TableAdapterManager.UpdateAll()` Methode):  
  
     [!code-csharp[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/CSharp/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.cs)]
     [!code-vb[VSProDataOrcasEndEditOnAll#2](../data-tools/codesnippet/VisualBasic/commit-in-process-edits-on-data-bound-controls-before-saving-data_2.vb)]  
  
## <a name="see-also"></a>Siehe auch  
 [Binden von Windows Forms-Steuerelementen an Daten in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Hierarchische Aktualisierung](../data-tools/hierarchical-update.md)