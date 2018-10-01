---
title: Commit in Bearbeitungen von datengebundenen Steuerelementen vor dem Speichern von Daten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- commiting edited records
- data-bound controls, in-process edits
- DataBinding class, commiting edited records
- hierarchical update, commiting edited records
- BindingSource class, commiting edited records
- EndEdit method
ms.assetid: 61af4798-eef7-468c-b229-5e1497febb2f
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bd56f9acfce7933d0bc89e7e86eb8083b9b1f867
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47512376"
---
# <a name="commit-in-process-edits-on-data-bound-controls-before-saving-data"></a>Ausführen eines Commits für aktuelle Bearbeitungen von datengebundenen Steuerelementen vor dem Speichern von Daten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Commit in Bearbeitungen von datengebundenen Steuerelementen vor dem Speichern von Daten](https://docs.microsoft.com/visualstudio/data-tools/commit-in-process-edits-on-data-bound-controls-before-saving-data).  
  
  
Beim Bearbeiten der Werte in datengebundenen Steuerelementen müssen Benutzer navigieren, aus der aktuellen Datensatz aus, um den aktualisierten Wert an der zugrunde liegenden Datenquelle zu committen, das das Steuerelement gebunden ist. Beim Ziehen von Elementen aus der [Fensters "Datenquellen"](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) auf ein Formular, das erste Element, das Sie löschen generiert den Code in die **speichern** click-Ereignis von der <xref:System.Windows.Forms.BindingNavigator>. Dieser Code Ruft die <xref:System.Windows.Forms.BindingSource.EndEdit%2A> Methode der <xref:System.Windows.Forms.BindingSource>. Aus diesem Grund wird der Aufruf von der <xref:System.Windows.Forms.BindingSource.EndEdit%2A> Methode wird nur für die erste generiert <xref:System.Windows.Forms.BindingSource> zum Formular hinzugefügt wird.  
  
 Die <xref:System.Windows.Forms.BindingSource.EndEdit%2A> Aufruf übernimmt alle Änderungen, die im Prozess, in dem alle datengebundenen Steuerelemente sind, das gerade bearbeitet werden. Aus diesem Grund verfügt ein vom datengebundenen Steuerelement immer noch den Fokus, und Sie klicken auf die **speichern** Schaltfläche, alle ausstehenden Änderungen im Steuerelement wird ein Commit ausgeführt, vor dem eigentlichen speichern (die `TableAdapterManager.UpdateAll` Methode).  
  
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

