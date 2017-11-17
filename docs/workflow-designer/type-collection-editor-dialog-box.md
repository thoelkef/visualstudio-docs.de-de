---
title: Typauflistungs-Editor (Dialogfeld) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: TypeCollectionEditor.UI
ms.assetid: 63cdea6b-bca2-4c06-b8b4-c8faabd40726
caps.latest.revision: "4"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: bdc27b59640d92507956030fc34c767e321a81fa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="type-collection-editor-dialog-box"></a>Typauflistungs-Editor (Dialogfeld)
Die **Typauflistungs-Editor** Dialogfeld wird verwendet, um bekannte Typen hinzuzufügen der **senden** und **Receive** Aktivitäten. Dieses Dialogfeld wird auch verwendet, um generische Typargumente hinzuzufügen der **InvokeMethod** Aktivität. Bei Verwendung für die **senden** und **Receive** Aktivitäten zum Hinzufügen bekannter Typen, die **Typauflistungs-Editor** Dialogfeld erfordert die Ergänzungen Typ eindeutig sein. Wenn ein doppelter Typ hinzugefügt und die Änderung wird ein Commit ausgeführt, indem Sie auf **OK**, wird eine Fehlermeldung zurückgegeben. Bei Verwendung für die **InvokeMethod** Aktivität zum Hinzufügen von generischen Typargumenten der **Typauflistungs-Editor** im Dialogfeld das Hinzufügen doppelter Typen zulässig.  
  
> [!NOTE]
>  [! UMFASSEN[Crabout](/dotnet/framework/wcf/feature-details/data-contract-known-types).  
  
 Die folgende Tabelle beschreibt die Elemente der Benutzeroberfläche (UI) von der **Typauflistung** (Dialogfeld).  
  
|Benutzeroberflächenelement|Beschreibung|  
|----------------|-----------------|  
|**Typliste**|Eine Liste der Typen, die hinzugefügt oder entfernt wurden.|  
  
## <a name="to-bring-up-the-type-collection-editor"></a>So öffnen Sie den Typauflistungs-Editor  
  
#### <a name="to-bring-up-the-type-collection-editor-for-the-send-and-receive-activities"></a>So öffnen Sie den Typauflistungs-Editor für die Send- und die Receive-Aktivität  
  
1.  Wählen Sie die **senden** oder **Receive** Aktivität in der Entwurfsansicht.  
  
2.  Drücken Sie **F4** um die **Eigenschaften** Fenster.  
  
3.  In der **Eigenschaften** Fenster, klicken Sie auf die Schaltfläche mit den Auslassungspunkten neben der **KnownTypes** Eigenschaft.  
  
#### <a name="to-bring-up-the-type-collection-editor-for-the-invokemethod-activity"></a>So öffnen Sie den Typauflistungs-Editor für die InvokeMethod-Aktivität  
  
1.  Wählen Sie die **InvokeMethod** Aktivität in der Entwurfsansicht.  
  
2.  Drücken Sie **F4** um die **Eigenschaften** Fenster.  
  
3.  In der **Eigenschaften** Fenster, klicken Sie auf die Schaltfläche mit den Auslassungspunkten neben der **GenericTypeArguments** Eigenschaft.