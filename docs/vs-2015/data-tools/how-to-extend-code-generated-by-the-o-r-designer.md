---
title: 'Vorgehensweise: Erweitern von durch den O / R-Designer erstellten Code | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: d6d1122e-2f55-4607-8d8b-48c3c22600fb
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3a5fc9bb7b6e2d6813c4c571633ef46d4b9e1f48
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2019
ms.locfileid: "59651733"
---
# <a name="how-to-extend-code-generated-by-the-or-designer"></a>Vorgehensweise: Erweitern von mit dem O/R-Designer erstellten Code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Code, der vom [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] generiert wurde, wird erneut generiert, wenn Änderungen an der Entitätsklasse und an anderen Objekten auf der Designeroberfläche vorgenommen werden. Aufgrund dieser erneuten Codegenerierung wird in der Regel jeglicher Code, der zum generierten Code hinzugefügt wurde, überschrieben, sobald vom Designer neuer Code generiert wird. Der [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] bietet die Möglichkeit, Dateien mit partiellen Klassen zu generieren, denen Code hinzugefügt werden kann, der nicht überschrieben wird. Ein Beispiel für das Hinzufügen eigenen Codes zu dem von [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] generierten Code, ist das Hinzufügen der Datenvalidierung zu LINQ to SQL-(Entitäts)-Klassen. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen von Validierungen zu Entitätsklassen](../data-tools/how-to-add-validation-to-entity-classes.md).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="adding-code-to-an-entity-class"></a>Hinzufügen von Code zu einer Entitätsklasse  
  
#### <a name="to-create-a-partial-class-and-add-code-to-an-entity-class"></a>So erstellen Sie eine partielle Klasse und fügen Code zu einer Entitätsklasse hinzu  
  
1.  Öffnen oder erstellen Sie eine neue LINQ to SQL-Klassendatei (**dbml** Datei) in der [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. (Doppelklicken Sie auf die **dbml** Datei **Projektmappen-Explorer**/**Datenbank-Explorer**.)  
  
2.  In der [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], mit der rechten Maustaste in der Klasse, die für die Sie zum Hinzufügen von Validierungen, und klicken Sie dann auf möchten **Ansichtscode**.  
  
     Der Code-Editor wird mit einer partiellen Klasse für die ausgewählte Entitätsklasse geöffnet.  
  
3.  Fügen Sie Ihren Code zur Deklaration der partiellen Klasse für die Entitätsklasse hinzu.  
  
## <a name="adding-code-to-a-datacontext"></a>Hinzufügen von Code zu einem DataContext  
  
#### <a name="to-create-a-partial-class-and-add-code-to-a-datacontext"></a>So erstellen Sie eine partielle Klasse und fügen Code zu einem DataContext hinzu  
  
1.  Öffnen oder erstellen Sie eine neue LINQ to SQL-Klassendatei (**dbml** Datei) in der [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. (Doppelklicken Sie auf die **dbml** Datei **Projektmappen-Explorer**/**Datenbank-Explorer**.)  
  
2.  In der [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]mit der rechten Maustaste auf einen leeren Bereich im Designer, und klicken Sie dann auf **Ansichtscode**.  
  
     Der Code-Editor wird mit einer partiellen Klasse für den DataContext geöffnet.  
  
3.  Fügen Sie Ihren Code zur Deklaration der partiellen Klasse für den DataContext hinzu.  
  
## <a name="see-also"></a>Siehe auch  
 [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen (O / R-Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Exemplarische Vorgehensweise: Hinzufügen von Validierungen zu Entitätsklassen](http://msdn.microsoft.com/library/85b06a02-b2e3-4534-95b8-d077c8d4c1d7)
