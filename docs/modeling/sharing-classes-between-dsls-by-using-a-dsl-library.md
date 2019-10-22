---
title: Gemeinsame Nutzung von Klassen durch DSLs über eine DSL-Bibliothek
ms.date: 11/04/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5293473e35424ccc6ee357d63a9355cacf0d6725
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670753"
---
# <a name="sharing-classes-between-dsls-by-using-a-dsl-library"></a>Gemeinsame Nutzung von Klassen durch DSLs über eine DSL-Bibliothek
Im Visual Studio-Visualisierungs-und Modellierungs-SDK können Sie eine unvollständige DSL-Definition erstellen, die Sie in eine andere DSL importieren können. Auf diese Weise können Sie allgemeine Teile von ähnlichen Modellen berücksichtigen.

## <a name="creating-and-using-dsl-libraries"></a>Erstellen und Verwenden von DSL-Bibliotheken

#### <a name="to-create-a-dsl-library"></a>So erstellen Sie eine DSL-Bibliothek

1. Erstellen Sie ein neues DSL-Projekt, und wählen Sie die Vorlage DSL Library Solution aus.

     Ein einzelnes DSL-Projekt wird mit einem leeren Modell erstellt.

2. Sie können Domänen Klassen, Beziehungen, Formen usw. hinzufügen.

     Die Elemente in der Bibliothek müssen keinen einzelnen Einbettungs Baum bilden.

     Um eine Beziehung zu definieren, die Importierer verwenden kann, erstellen Sie zwei Domänen Klassen, und erstellen Sie die Beziehung zwischen Ihnen.

     Legen Sie den **Vererbungsmodifizierer** der Domänen Klassen auf `Abstract` fest.

3. Sie können Elemente hinzufügen, die Sie im DSL-Explorer definieren, z. b. Verbindungs-Generatoren.

4. Sie können Anpassungen hinzufügen, die zusätzlichen Code erfordern, z. b. Validierungs Einschränkungen.

5. Klicken Sie auf **alle Vorlagen transformieren**.

6. Erstellen Sie das Projekt.

7. Wenn Sie die DSL für andere zu verwendende Personen verteilen, müssen Sie sowohl die kompilierte Assembly (dll) als auch die Datei `DslDefinition.dsl` bereitstellen. Sie finden die kompilierte Assembly in einem Ordner unter `Dsl\bin\*`

#### <a name="to-import-a-dsl-library"></a>So importieren Sie eine DSL-Bibliothek

1. Klicken Sie in einer anderen DSL-Definition im **DSL-Explorer**mit der rechten Maustaste auf die Stamm Klasse der DSL, und klicken Sie dann auf **neuen dsllibrary-Import hinzufügen**.

2. Legen Sie in der Eigenschaftenfenster den **Dateipfad** der Bibliothek fest. Sie können entweder einen relativen oder einen absoluten Pfad verwenden.

    Die importierte Bibliothek wird im DSL-Explorer im schreibgeschützten Modus angezeigt.

3. Sie können die importierten Klassen als Basisklassen verwenden. Erstellen Sie eine Domänen Klasse in der importierten DSL, und legen Sie in der Eigenschaftenfenster **Basisklasse** auf eine importierte Klasse fest.

4. Klicken Sie auf alle Vorlagen transformieren.

5. Fügen Sie dem DSL-Projekt einen Verweis auf die Assembly (dll) hinzu, die vom DSL-Bibliotheksprojekt erstellt wurde.

6. Erstellen Sie die Projektmappe.

   In einer DSL-Bibliothek können andere Bibliotheken importiert werden. Wenn Sie eine Bibliothek importieren, werden die zugehörigen Importe auch automatisch im DSL-Explorer angezeigt.

## <a name="see-also"></a>Siehe auch

- [So definieren Sie eine domänenspezifische Sprache](../modeling/how-to-define-a-domain-specific-language.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
