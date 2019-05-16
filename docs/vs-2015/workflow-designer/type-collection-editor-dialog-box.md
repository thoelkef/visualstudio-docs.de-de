---
title: Typauflistungs-Editor (Dialogfeld) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- TypeCollectionEditor.UI
ms.assetid: 63cdea6b-bca2-4c06-b8b4-c8faabd40726
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: be2e6bde6c25c1bb515ec3f017f14506c03a3a71
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697066"
---
# <a name="type-collection-editor-dialog-box"></a>Typauflistungs-Editor (Dialogfeld)
Die **Typauflistungs-Editor** Dialogfeld wird verwendet, um bekannte Typen hinzugefügt der **senden** und **Receive** Aktivitäten. Dieses Dialogfeld wird auch verwendet, um generische Typargumente hinzuzufügen der **InvokeMethod** Aktivität. Bei Verwendung für die **senden** und **Receive** Aktivitäten, die bekannte Typen hinzufügen der **Typauflistungs-Editor** Dialogfeld erfordert die typhinzufügungen hier eindeutig sein. Wenn ein doppelter Typ hinzugefügt wird, und die Änderung wird ein Commit ausgeführt, indem Sie auf **OK**, wird eine Fehlermeldung zurückgegeben. Bei Verwendung für die **InvokeMethod** Aktivität zum Hinzufügen von generischen Typargumenten, die **Typauflistungs-Editor** Dialogfeld ermöglicht das Hinzufügen doppelter Typen.  
  
> [!NOTE]
> [!INCLUDE[crabout](../includes/crabout-md.md)] zu bekannten Typen finden Sie unter [Data Contract Known Types](https://msdn.microsoft.com/library/1a0baea1-27b7-470d-9136-5bbad86c4337)exportiert werden.  
  
 Die folgende Tabelle beschreibt die Elemente der Benutzeroberfläche (UI) von der **Typauflistung** Dialogfeld.  
  
|Benutzeroberflächenelement|Beschreibung|  
|----------------|-----------------|  
|**Typliste**|Eine Liste der Typen, die hinzugefügt oder entfernt wurden.|  
  
## <a name="to-bring-up-the-type-collection-editor"></a>So öffnen Sie den Typauflistungs-Editor  
  
#### <a name="to-bring-up-the-type-collection-editor-for-the-send-and-receive-activities"></a>So öffnen Sie den Typauflistungs-Editor für die Send- und die Receive-Aktivität  
  
1. Wählen Sie die **senden** oder **Receive** Aktivität in der Entwurfsansicht.  
  
2. Drücken Sie **F4** um die **Eigenschaften** Fenster.  
  
3. In der **Eigenschaften** Fenster, klicken Sie auf die Schaltfläche mit den Auslassungspunkten neben der **KnownTypes** Eigenschaft.  
  
#### <a name="to-bring-up-the-type-collection-editor-for-the-invokemethod-activity"></a>So öffnen Sie den Typauflistungs-Editor für die InvokeMethod-Aktivität  
  
1. Wählen Sie die **InvokeMethod** Aktivität in der Entwurfsansicht.  
  
2. Drücken Sie **F4** um die **Eigenschaften** Fenster.  
  
3. In der **Eigenschaften** Fenster, klicken Sie auf die Schaltfläche mit den Auslassungspunkten neben der **GenericTypeArguments** Eigenschaft.