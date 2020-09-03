---
title: 'Gewusst wie: Erweitern von durch den O-R-Designer generierten Code | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: d6d1122e-2f55-4607-8d8b-48c3c22600fb
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a1d60090ca16907e16bb58970d793124c5bb2dec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665950"
---
# <a name="how-to-extend-code-generated-by-the-or-designer"></a>Gewusst wie: Erweitern von durch den O/R-Designer erstellten Code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Code, der vom [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] generiert wurde, wird erneut generiert, wenn Änderungen an der Entitätsklasse und an anderen Objekten auf der Designeroberfläche vorgenommen werden. Aufgrund dieser erneuten Codegenerierung wird in der Regel jeglicher Code, der zum generierten Code hinzugefügt wurde, überschrieben, sobald vom Designer neuer Code generiert wird. Der [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] bietet die Möglichkeit, Dateien mit partiellen Klassen zu generieren, denen Code hinzugefügt werden kann, der nicht überschrieben wird. Ein Beispiel für das Hinzufügen eigenen Codes zu dem von [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] generierten Code, ist das Hinzufügen der Datenvalidierung zu LINQ to SQL-(Entitäts)-Klassen. Weitere Informationen finden Sie unter Gewusst [wie: Hinzufügen von Validierungen zu Entitäts Klassen](../data-tools/how-to-add-validation-to-entity-classes.md).

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="adding-code-to-an-entity-class"></a>Hinzufügen von Code zu einer Entitätsklasse

#### <a name="to-create-a-partial-class-and-add-code-to-an-entity-class"></a>So erstellen Sie eine partielle Klasse und fügen Code zu einer Entitätsklasse hinzu

1. Öffnen Sie, oder erstellen Sie eine neue LINQ to SQL Klassen-Datei (**. dbml** -Datei) in der [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . (Doppelklicken Sie auf die **DBML** -Datei in **Projektmappen-Explorer** / **Datenbank-Explorer**.)

2. Klicken Sie in der mit der [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] rechten Maustaste auf die Klasse, für die Sie die Validierung hinzufügen möchten, und klicken Sie dann auf **Code anzeigen**.

     Der Code-Editor wird mit einer partiellen Klasse für die ausgewählte Entitätsklasse geöffnet.

3. Fügen Sie Ihren Code zur Deklaration der partiellen Klasse für die Entitätsklasse hinzu.

## <a name="adding-code-to-a-datacontext"></a>Hinzufügen von Code zu einem DataContext

#### <a name="to-create-a-partial-class-and-add-code-to-a-datacontext"></a>So erstellen Sie eine partielle Klasse und fügen Code zu einem DataContext hinzu

1. Öffnen Sie, oder erstellen Sie eine neue LINQ to SQL Klassen-Datei (**. dbml** -Datei) in der [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . (Doppelklicken Sie auf die **DBML** -Datei in **Projektmappen-Explorer** / **Datenbank-Explorer**.)

2. Klicken Sie in der mit der [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] rechten Maustaste auf einen leeren Bereich im Designer, und klicken Sie dann auf **Code anzeigen**.

     Der Code-Editor wird mit einer partiellen Klasse für den DataContext geöffnet.

3. Fügen Sie Ihren Code zur Deklaration der partiellen Klasse für den DataContext hinzu.

## <a name="see-also"></a>Weitere Informationen
 [LINQ to SQL Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) Exemplarische Vorgehensweise [: Erstellen von LINQ to SQL Klassen (O-R-Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) Exemplarische Vorgehensweise [: Hinzufügen von Validierung zu Entitäts Klassen](https://msdn.microsoft.com/library/85b06a02-b2e3-4534-95b8-d077c8d4c1d7)
