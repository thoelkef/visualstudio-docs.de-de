---
title: Gemeinsame Nutzung von Klassen durch die Verwendung einer Bibliothek DSL DSLs | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 935862ec8bbe79634595d547067204c9893a4944
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2018
---
# <a name="sharing-classes-between-dsls-by-using-a-dsl-library"></a>Gemeinsame Nutzung von Klassen durch DSLs über eine DSL-Bibliothek
In der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Visualization and Modeling SDK können Sie erstellen eine unvollständige DSL-Definition, die in einer anderen DSL importiert werden können. Dadurch können Sie die allgemeinen Teile der ähnlichen Modellen zu berücksichtigen.  
  
## <a name="creating-and-using-dsl-libraries"></a>Erstellen und Verwenden von DSL-Bibliotheken  
  
#### <a name="to-create-a-dsl-library"></a>So erstellen Sie einen DSL-Bibliothek  
  
1.  Erstellen eines neuen DSL-Projekts, und wählen Sie die Projektmappe (Vorlage) DSL-Bibliothek.  
  
     Ein einzelnes DSL-Projekt wird mit einem leeren Modell erstellt werden.  
  
2.  Sie können Domänenklassen, Beziehungen, Formen usw. hinzufügen.  
  
     Die Elemente in der Bibliothek keine bilden eine einzelne Struktur einbetten.  
  
     Um eine Beziehung zu definieren, die Importer verwenden können, erstellen Sie zwei Domänenklassen, und erstellen Sie die Beziehung zwischen ihnen.  
  
     Legen Sie die **Inheritance Modifier** der Domänenklassen zu `Abstract`.  
  
3.  Sie können Elemente hinzufügen, die Sie im Explorer für DSL, z. B. Verbindungs-Generatoren zu definieren.  
  
4.  Sie können Anpassungen hinzufügen, die zusätzlichen Code, z. B. validierungseinschränkungen erfordern.  
  
5.  Klicken Sie auf **Transformieren aller Vorlagen**.  
  
6.  Erstellen Sie das Projekt.  
  
7.  Wenn Sie die DSL für andere Benutzer verteilen, müssen Sie die kompilierte Assembly (DLL) und die Datei bereitstellen `DslDefinition.dsl`. Sie können die kompilierte Assembly in einem Ordner unter Suchen.`Dsl\bin\*`  
  
#### <a name="to-import-a-dsl-library"></a>Eine DSL-Bibliothek importieren  
  
1.  In einer anderen DSL-Definition in **Explorer für DSL**mit der rechten Maustaste auf die Stammklasse der DSL, und klicken Sie dann auf **Hinzufügen neuer DslLibrary Import**.  
  
2.  Legen Sie im Fenster Eigenschaften die **Dateipfad** der Bibliothek. Sie können einen relativen oder einen absoluten Pfad verwenden.  
  
     Die importierten Bibliothek, die im Nur-Lese-Modus im DSL-Explorer angezeigt werden.  
  
3.  Sie können die importierten Klassen als Basisklassen verwenden. Erstellen Sie eine Domänenklasse, in den Import von DSL, und legen Sie im Eigenschaftenfenster im Fenster **Basisklasse** auf eine importierte Klasse.  
  
4.  Klicken Sie auf Transformieren aller Vorlagen.  
  
5.  Fügen Sie dem DSL-Projekt einen Verweis auf die Assembly (DLL), die von der DSL Bibliotheksprojekt erstellt wurde.  
  
6.  Erstellen Sie die Projektmappe.  
  
 Eine DSL-Bibliothek können andere Bibliotheken importieren. Wenn Sie eine Bibliothek importieren, werden seine Importe auch automatisch im DSL-Explorer angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [So definieren Sie eine domänenspezifische Sprache](../modeling/how-to-define-a-domain-specific-language.md)
 
[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
