---
title: Workflow-Designer - Typauflistungs-Editor (Dialogfeld)
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- TypeCollectionEditor.UI
ms.assetid: 63cdea6b-bca2-4c06-b8b4-c8faabd40726
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 08c6e8e2f7851d74bfbeb0399dd758ae0ca25b4f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49812747"
---
# <a name="type-collection-editor-dialog-box"></a>Typauflistungs-Editor (Dialogfeld)

Die **Typauflistungs-Editor** Dialogfeld wird verwendet, um bekannte Typen hinzugefügt der **senden** und **Receive** Aktivitäten. Dieses Dialogfeld wird auch verwendet, um generische Typargumente hinzuzufügen der **InvokeMethod** Aktivität. Bei Verwendung für die **senden** und **Receive** Aktivitäten, die bekannte Typen hinzufügen der **Typauflistungs-Editor** Dialogfeld erfordert die typhinzufügungen hier eindeutig sein. Wenn ein doppelter Typ hinzugefügt wird, und die Änderung wird ein Commit ausgeführt, indem Sie auf **OK**, wird eine Fehlermeldung zurückgegeben. Bei Verwendung für die **InvokeMethod** Aktivität zum Hinzufügen von generischen Typargumenten, die **Typauflistungs-Editor** Dialogfeld ermöglicht das Hinzufügen doppelter Typen.

Weitere Informationen finden Sie unter [bekannte Typen in Datenverträgen](/dotnet/framework/wcf/feature-details/data-contract-known-types).

Die folgende Tabelle beschreibt die Elemente der Benutzeroberfläche (UI) von der **Typauflistung** Dialogfeld.

|Benutzeroberflächenelement|Beschreibung|
|-|-----------------|
|**Typliste**|Eine Liste der Typen, die hinzugefügt oder entfernt wurden.|

## <a name="to-bring-up-the-type-collection-editor-for-the-send-and-receive-activities"></a>So öffnen Sie den Typauflistungs-Editor für die Send- und die Receive-Aktivität

1.  Wählen Sie die **senden** oder **Receive** Aktivität in der Entwurfsansicht.

2.  Drücken Sie **F4** um die **Eigenschaften** Fenster.

3.  In der **Eigenschaften** Fenster, klicken Sie auf die Schaltfläche mit den Auslassungspunkten neben der **KnownTypes** Eigenschaft.

## <a name="to-bring-up-the-type-collection-editor-for-the-invokemethod-activity"></a>So öffnen Sie den Typauflistungs-Editor für die InvokeMethod-Aktivität

1.  Wählen Sie die **InvokeMethod** Aktivität in der Entwurfsansicht.

2.  Drücken Sie **F4** um die **Eigenschaften** Fenster.

3.  In der **Eigenschaften** Fenster, klicken Sie auf die Schaltfläche mit den Auslassungspunkten neben der **GenericTypeArguments** Eigenschaft.