---
title: Typauflistungs-Editor (Dialog Feld) Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- TypeCollectionEditor.UI
ms.assetid: 63cdea6b-bca2-4c06-b8b4-c8faabd40726
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: dae99166b8b811df75f2e2777d176e6778b60c7d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670150"
---
# <a name="type-collection-editor-dialog-box"></a>Typauflistungs-Editor (Dialogfeld)
Das Dialogfeld typauflistungs- **Editor** wird verwendet, um den **Sende** -und **Empfangs** Aktivitäten bekannte Typen hinzuzufügen. Dieses Dialogfeld wird auch verwendet, um der **InvokeMethod** -Aktivität generische Typargumente hinzuzufügen. Wenn für die **Sende** -und **Empfangs** Aktivitäten verwendet wird, um bekannte Typen hinzuzufügen, muss im Dialogfeld typauflistungs- **Editor** die typergänzungen eindeutig sein. Wenn ein doppelter Typ hinzugefügt und für die Änderung ein Commit ausgeführt wird, indem Sie auf **OK**klicken, wird eine Fehlermeldung zurückgegeben. Bei Verwendung für die **InvokeMethod** -Aktivität zum Hinzufügen von generischen Typargumenten ermöglicht das Dialogfeld typauflistungs- **Editor** das Hinzufügen doppelter Typen.

> [!NOTE]
> [!INCLUDE[crabout](../includes/crabout-md.md)] zu bekannten Typen finden Sie unter [Data Contract Known Types](https://msdn.microsoft.com/library/1a0baea1-27b7-470d-9136-5bbad86c4337)exportiert werden.

 In der folgenden Tabelle werden die Benutzeroberflächen Elemente des Dialog Felds **Typsammlung** beschrieben.

|Benutzeroberflächenelement|BESCHREIBUNG|
|----------------|-----------------|
|**Type List**|Eine Liste der Typen, die hinzugefügt oder entfernt wurden.|

## <a name="to-bring-up-the-type-collection-editor"></a>So öffnen Sie den Typauflistungs-Editor

#### <a name="to-bring-up-the-type-collection-editor-for-the-send-and-receive-activities"></a>So öffnen Sie den Typauflistungs-Editor für die Send- und die Receive-Aktivität

1. Wählen Sie die **Sende** -oder **Empfangs** Aktivität in der Entwurfs Ansicht aus.

2. Drücken Sie **F4** , um das **Eigenschaften** Fenster zu aktivieren.

3. Klicken Sie im **Eigenschaften** Fenster neben der **KnownTypes** -Eigenschaft auf die Schaltfläche mit den Auslassungs Punkten.

#### <a name="to-bring-up-the-type-collection-editor-for-the-invokemethod-activity"></a>So öffnen Sie den Typauflistungs-Editor für die InvokeMethod-Aktivität

1. Wählen Sie die **InvokeMethod** -Aktivität in der Entwurfs Ansicht aus.

2. Drücken Sie **F4** , um das **Eigenschaften** Fenster zu aktivieren.

3. Klicken Sie im **Eigenschaften** Fenster auf die Schaltfläche mit den Auslassungs Punkten neben der Eigenschaft **genericTypeArguments** .