---
title: Gemeinsame Nutzung von Klassen durch DSLs über eine DSL-Bibliothek
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 36c49d3447a5f1fafcf4601057c66ebedcb193ec
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63003382"
---
# <a name="sharing-classes-between-dsls-by-using-a-dsl-library"></a>Gemeinsame Nutzung von Klassen durch DSLs über eine DSL-Bibliothek
In Visual Studio-Visualisierungs- und Modellierungs-SDK können Sie eine unvollständige DSL-Definition erstellen, die Sie in einer anderen DSL importieren können. Dadurch können Sie die allgemeinen Teile der ähnlichen Modellen zu berücksichtigen.

## <a name="creating-and-using-dsl-libraries"></a>Erstellen und verwenden die DSL-Bibliotheken

#### <a name="to-create-a-dsl-library"></a>Um eine DSL-Bibliothek zu erstellen.

1. Erstellen eines neuen DSL-Projekts, und wählen Sie die Lösungsvorlage für die DSL-Bibliothek.

     Ein einzelnes DSL-Projekt wird mit einem leeren Modell erstellt.

2. Sie können Domänenklassen, Beziehungen, Formen und so weiter hinzufügen.

     Die Elemente in der Bibliothek keine einzelne einbettende Struktur bilden.

     Um eine Beziehung zu definieren, die Importers verwenden können, erstellen Sie zwei Domänenklassen, und erstellen Sie die Beziehung zwischen ihnen.

     Neben der Einstellung der **Vererbungsmodifizierer** der Domänenklassen, `Abstract`.

3. Sie können Elemente hinzufügen, die Sie im DSL-Explorer, wie z. B. Verbindungs-Generatoren zu definieren.

4. Sie können Anpassungen hinzufügen, die zusätzlichen Code, z. B. validierungseinschränkungen erfordern.

5. Klicken Sie auf **alle Vorlagen transformieren**.

6. Erstellen Sie das Projekt.

7. Wenn Sie die DSL für andere Benutzer verteilen, müssen Sie sowohl die kompilierte Assembly (DLL) und die Datei bereitstellen `DslDefinition.dsl`. Sie können die kompilierte Assembly in einem Ordner unter finden. `Dsl\bin\*`

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

- [So definieren Sie eine domänenspezifische Sprache](../modeling/how-to-define-a-domain-specific-language.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
