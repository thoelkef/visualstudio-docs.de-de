---
title: Gemeinsame Nutzung von Klassen durch DSLs über eine DSL-Bibliothek | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 509bd96b-3e66-47f4-8642-771421d0d0d5
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0c3a14a254eb3b07a95687faaf377664dd6f747a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58958941"
---
# <a name="sharing-classes-between-dsls-by-using-a-dsl-library"></a>Gemeinsame Nutzung von Klassen durch DSLs über eine DSL-Bibliothek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Visualisierungs- und Modellierungs-SDK können Sie erstellen eine unvollständige DSL-Definition, die Sie in einer anderen DSL importieren können. Dadurch können Sie die allgemeinen Teile der ähnlichen Modellen zu berücksichtigen.  
  
## <a name="creating-and-using-dsl-libraries"></a>Erstellen und verwenden die DSL-Bibliotheken  
  
#### <a name="to-create-a-dsl-library"></a>Um eine DSL-Bibliothek zu erstellen.  
  
1.  Erstellen eines neuen DSL-Projekts, und wählen Sie die Lösungsvorlage für die DSL-Bibliothek.  
  
     Ein einzelnes DSL-Projekt wird mit einem leeren Modell erstellt.  
  
2.  Sie können Domänenklassen, Beziehungen, Formen und so weiter hinzufügen.  
  
     Die Elemente in der Bibliothek keine einzelne einbettende Struktur bilden.  
  
     Um eine Beziehung zu definieren, die Importers verwenden können, erstellen Sie zwei Domänenklassen, und erstellen Sie die Beziehung zwischen ihnen.  
  
     Neben der Einstellung der **Vererbungsmodifizierer** der Domänenklassen, `Abstract`.  
  
3.  Sie können Elemente hinzufügen, die Sie im DSL-Explorer, wie z. B. Verbindungs-Generatoren zu definieren.  
  
4.  Sie können Anpassungen hinzufügen, die zusätzlichen Code, z. B. validierungseinschränkungen erfordern.  
  
5.  Klicken Sie auf **alle Vorlagen transformieren**.  
  
6.  Erstellen Sie das Projekt.  
  
7.  Wenn Sie die DSL für andere Benutzer verteilen, müssen Sie sowohl die kompilierte Assembly (DLL) und die Datei bereitstellen `DslDefinition.dsl`. Sie können die kompilierte Assembly in einem Ordner unter finden. `Dsl\bin\*`  
  
#### <a name="to-import-a-dsl-library"></a>So importieren Sie eine DSL-Bibliothek  
  
1. In einer anderen DSL-Definition in **DSL-Explorer**mit der rechten Maustaste auf die Stammklasse der DSL, und klicken Sie dann auf **Hinzufügen eines neuen DslLibrary Import**.  
  
2. Legen Sie im Fenster Eigenschaften die **Dateipfad** der Bibliothek. Sie können ein relativer oder absoluter Pfad.  
  
    Die importierte Bibliothek wird im DSL-Explorer im schreibgeschützten Modus angezeigt.  
  
3. Sie können die importierten Klassen als Basisklassen verwenden. Erstellen Sie eine Domänenklasse in der importierenden DSL, und legen in den Eigenschaften des **Basisklasse** zu einer Klasse importiert.  
  
4. Klicken Sie auf alle Vorlagen transformieren.  
  
5. Fügen Sie dem DSL-Projekt einen Verweis auf die Assembly (DLL), die von der DSL-Bibliothek-Projekt erstellt wurde.  
  
6. Erstellen Sie die Projektmappe.  
  
   Eine DSL-Bibliothek können andere Bibliotheken importieren. Wenn Sie eine Bibliothek importieren, werden die Importe auch automatisch im DSL-Explorer angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [So definieren Sie eine domänenspezifische Sprache](../modeling/how-to-define-a-domain-specific-language.md)
