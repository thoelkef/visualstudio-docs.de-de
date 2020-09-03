---
title: Freigeben von Klassen zwischen DSLs mithilfe einer DSL-Bibliothek | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 509bd96b-3e66-47f4-8642-771421d0d0d5
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 093cc277fa1cbe1915099fd9663fc1ccb797ca3a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671185"
---
# <a name="sharing-classes-between-dsls-by-using-a-dsl-library"></a>Gemeinsame Nutzung von Klassen durch DSLs über eine DSL-Bibliothek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Im [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Visualisierungs-und Modellierungs-SDK können Sie eine unvollständige DSL-Definition erstellen, die Sie in eine andere DSL importieren können. Auf diese Weise können Sie allgemeine Teile von ähnlichen Modellen berücksichtigen.

## <a name="creating-and-using-dsl-libraries"></a>Erstellen und Verwenden von DSL-Bibliotheken

#### <a name="to-create-a-dsl-library"></a>So erstellen Sie eine DSL-Bibliothek

1. Erstellen Sie ein neues DSL-Projekt, und wählen Sie die Vorlage DSL Library Solution aus.

     Ein einzelnes DSL-Projekt wird mit einem leeren Modell erstellt.

2. Sie können Domänen Klassen, Beziehungen, Formen usw. hinzufügen.

     Die Elemente in der Bibliothek müssen keinen einzelnen Einbettungs Baum bilden.

     Um eine Beziehung zu definieren, die Importierer verwenden kann, erstellen Sie zwei Domänen Klassen, und erstellen Sie die Beziehung zwischen Ihnen.

     Legen Sie den **Vererbungsmodifizierer** der Domänen Klassen auf fest `Abstract` .

3. Sie können Elemente hinzufügen, die Sie im DSL-Explorer definieren, z. b. Verbindungs-Generatoren.

4. Sie können Anpassungen hinzufügen, die zusätzlichen Code erfordern, z. b. Validierungs Einschränkungen.

5. Klicken Sie auf **alle Vorlagen transformieren**.

6. Erstellen Sie das Projekt.

7. Wenn Sie die DSL für andere zu verwendende Personen verteilen, müssen Sie sowohl die kompilierte Assembly (dll) als auch die Datei bereitstellen `DslDefinition.dsl` . Sie finden die kompilierte Assembly in einem Ordner unter `Dsl\bin\*`

#### <a name="to-import-a-dsl-library"></a>So importieren Sie eine DSL-Bibliothek

1. Klicken Sie in einer anderen DSL-Definition im **DSL-Explorer**mit der rechten Maustaste auf die Stamm Klasse der DSL, und klicken Sie dann auf **neuen dsllibrary-Import hinzufügen**.

2. Legen Sie in der Eigenschaftenfenster den **Dateipfad** der Bibliothek fest. Sie können entweder einen relativen oder einen absoluten Pfad verwenden.

    Die importierte Bibliothek wird im DSL-Explorer im schreibgeschützten Modus angezeigt.

3. Sie können die importierten Klassen als Basisklassen verwenden. Erstellen Sie eine Domänen Klasse in der importierten DSL, und legen Sie in der Eigenschaftenfenster **Basisklasse** auf eine importierte Klasse fest.

4. Klicken Sie auf Alle Vorlagen transformieren.

5. Fügen Sie dem DSL-Projekt einen Verweis auf die Assembly (dll) hinzu, die vom DSL-Bibliotheksprojekt erstellt wurde.

6. Erstellen Sie die Projektmappe.

   In einer DSL-Bibliothek können andere Bibliotheken importiert werden. Wenn Sie eine Bibliothek importieren, werden die zugehörigen Importe auch automatisch im DSL-Explorer angezeigt.

## <a name="see-also"></a>Weitere Informationen
 [So definieren Sie eine domänenspezifische Sprache](../modeling/how-to-define-a-domain-specific-language.md)
