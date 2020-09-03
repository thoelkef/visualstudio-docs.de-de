---
title: Definieren von Paketen und Namespaces | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, namespaces
- UML, namespaces
- UML, packages
- UML model, packages
ms.assetid: 79147068-02d5-4b70-933d-f647c1da3829
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 657bb91295134352fb00649ad06f59e34593c578
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669903"
---
# <a name="define-packages-and-namespaces"></a>Definieren von Paketen und Namespaces
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio ist ein *Paket* ein Container für die Definitionen von UML-Elementen, z. b. Klassen, Anwendungsfälle und Komponenten. Ein Paket kann auch andere Pakete enthalten.

 Im UML-Modell-Explorer werden alle Definitionen in einem Paket unter dem Paket geschachtelt. Das UML-Modell ist eine Art von Paket und bildet den Stamm der Struktur.

 Welche Versionen von Visual Studio dieses Feature unterstützen, erfahren Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="in-this-topic"></a>In diesem Thema
 [Namespaces](#Namespaces)

 [Erstellen und Anzeigen von Paketen](#Packages)

 [Erstellen von Modellelementen in Paketen](#Elements)

 [Verschieben von Elementen in Pakete und aus Paketen](#Moving)

 [Einfügen von Elementen in ein Paket](#Pasting)

 [Importbeziehungen zwischen Paketen](#Import)

 [Verweise von einem Namespace auf einen anderen Namespace](#References)

 [Eigenschaften von Paketen](#Properties)

## <a name="namespaces"></a><a name="Namespaces"></a> Namespaces
 Mit Paketen lässt sich Arbeit in unterschiedliche Bereiche aufteilen. Jedes Paket definiert einen Namespace, damit keine Konflikte zwischen Namen auftreten, die in anderen Paketen definiert sind.

 Die Eigenschaft für den qualifizierten Namen jedes Elements ist der qualifizierte Name des Pakets, zu dem es gehört, gefolgt vom eigenen Namen des Elements. Wenn der Name des Pakets `MyPackage` lautet, lautet der qualifizierte Name einer Klasse in dem Paket beispielsweise `MyPackage::MyClass`. Da jedes Element in einem Modell enthalten ist, beginnt jeder qualifizierte Name mit dem Namen des Modells.

 Ein Modell definiert auch einen Namespace, sodass der qualifizierte Name jedes Elements in einem Modell mit dem Namen des Modells beginnt.

 Andere Modellelemente definieren ebenfalls Namespaces. Beispielsweise gehört ein Vorgang zu dem von der übergeordneten Klasse des Vorgangs definierten Namespace, sodass sein qualifizierter Name etwa `MyModel ::MyPackage ::MyClass ::MyOperation` lautet. Entsprechend gehört eine Aktion zu dem Namespace, der von der übergeordneten Aktivität der Aktion definiert wird.

 Pakete sind Container. Wenn Sie ein Paket verschieben oder löschen, werden die Klassen, Pakete und andere im Paket definierten Elemente ebenfalls verschoben bzw. gelöscht. Das Gleiche gilt für andere Elemente, die Namespaces definieren.

## <a name="creating-and-viewing-packages"></a><a name="Packages"></a> Erstellen und Anzeigen von Paketen
 Sie können ein Paket in einem UML-Klassendiagramm oder im UML-Modell-Explorer erstellen.

#### <a name="to-create-a-package-in-a-uml-class-diagram"></a>So erstellen Sie ein Paket in einem UML-Klassendiagramm

1. Öffnen Sie ein UML-Klassendiagramm, oder erstellen Sie ein neues UML-Klassendiagramm.

2. Klicken Sie auf das **Paket** Tool.

3. Klicken Sie auf eine beliebige Stelle im Diagramm. Eine neue Paketform wird angezeigt.

     Sie können in ein vorhandenes Paket klicken, um ein Paket in einem anderen Paket zu schachteln.

4. Geben Sie einen neuen Namen für das Paket ein.

#### <a name="to-create-a-package-in-uml-model-explorer"></a>So erstellen Sie ein Paket im UML-Modell-Explorer

1. Öffnet den **UML-Modell-Explorer**. Zeigen Sie im Menü **Architektur** auf **Fenster**, und klicken Sie dann auf den UML- **Modell-Explorer**.

2. Klicken Sie mit der rechten Maustaste auf ein Paket oder Modell, dem Sie ein neues Paket hinzufügen möchten.

   > [!NOTE]
   > Sie können ein Paket in einem anderen Paket schachteln.

3. Zeigen Sie auf **Hinzufügen** , und klicken Sie auf **Paket**.

    Im Modell wird ein neues Paket angezeigt.

4. Geben Sie einen neuen Namen für das Paket ein.

   Wenn Sie im UML-Modell-Explorer ein Paket erstellt haben, können Sie es in einem UML-Klassendiagramm anzeigen. Sie können ein Paket auch in mehreren UML-Klassendiagrammen anzeigen.

#### <a name="to-show-an-existing-package-on-a-uml-class-diagram"></a>So zeigen Sie ein vorhandenes Paket in einem UML-Klassendiagramm an

- Ziehen Sie das Paket aus dem UML-Modell-Explorer in das Klassendiagramm.

    > [!NOTE]
    > Hierdurch wird in diesem Diagramm eine Ansicht des Pakets erstellt. In der Ansicht werden nicht unbedingt alle im Paket enthaltenen Elemente angezeigt. Um sicherzustellen, dass der gesamte Inhalt eines Pakets angezeigt wird, zeigen Sie das Paket im UML-Modell-Explorer an.

## <a name="creating-model-elements-inside-packages"></a><a name="Elements"></a> Erstellen von Modellelementen innerhalb von Paketen
 Es gibt vier Verfahren, mit denen Sie Modellelemente in ein Paket einfügen können:

- Fügen Sie im UML-Modell-Explorer einem Paket ein neues Element hinzu.

- Fügen Sie in einem UML-Klassendiagramm Paketen Klassen und andere Typen hinzu.

- Legen Sie die **LinkedPackage** -Eigenschaft eines Diagramms fest, damit neue Elemente, die im Diagramm erstellt werden, in das von Ihnen angegebene Paket eingefügt werden. Klassendiagramme, Komponentendiagramme und Anwendungsfalldiagramme können auf diese Weise mit einem Paket verknüpft werden.

- Verschieben Sie im UML-Modell-Explorer Elemente in ein Paket oder aus einem Paket.

  Im UML-Modell-Explorer wird ein Element in einem Paket unter dem Paket angezeigt, und sein qualifizierter Name beginnt mit dem qualifizierten Namen des Pakets. Um den qualifizierten Namen eines beliebigen Elements anzuzeigen, klicken Sie mit der rechten Maustaste auf das Element, und klicken Sie dann auf **Eigenschaften**. Die Eigenschaft **qualifizierter Name** wird im Fenster **Eigenschaften** angezeigt.

#### <a name="to-create-an-element-in-a-package-in-uml-model-explorer"></a>So erstellen Sie im UML-Modell-Explorer ein Element in einem Paket

1. Öffnet den **UML-Modell-Explorer**. Zeigen Sie im Menü **Ansicht** auf **Weitere Fenster**, und klicken Sie dann auf **UML-Modell-Explorer**.

2. Klicken Sie mit der rechten Maustaste auf ein Paket oder Modell, dem Sie ein neues Element hinzufügen möchten.

3. Zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf die Art des Elements, das Sie hinzufügen möchten.

     Das neue Element wird unter dem Paket angezeigt.

4. Geben Sie einen Namen für das neue Element ein.

    > [!NOTE]
    > Das neue Element wird in keinem Diagramm angezeigt. Um eine Ansicht des neuen Elements zu erstellen, können Sie es aus dem UML-Modell-Explorer in ein Diagramm ziehen. Das Diagramm muss von einem Diagrammtyp sein, in dem diese Art von Element angezeigt wird.

#### <a name="to-create-an-element-in-a-package-on-a-uml-class-diagram"></a>So erstellen Sie in einem UML-Klassendiagramm ein Element in einem Paket

1. Öffnen Sie ein Klassendiagramm, in dem das Paket angezeigt wird.

    - Erstellen Sie ein neues Paket, sofern Sie noch kein neues Paket erstellt haben.

    - Damit ein vorhandenes Paket in einem Klassendiagramm angezeigt wird, können Sie das Paket aus dem **UML-Modell-Explorer** in das Klassendiagramm ziehen.

2. Klicken Sie auf das Tool für eine Klasse, eine Schnittstelle, eine Enumeration oder ein Paket.

3. Klicken Sie auf das Paket, in das Sie das neue Element einfügen möchten.

     Das neue Element wird in dem Paket angezeigt.

#### <a name="to-create-all-the-elements-of-a-diagram-in-a-specified-package"></a>So erstellen Sie alle Elemente eines Diagramms in einem angegebenen Paket

1. Erstellen Sie das Paket, sofern Sie es noch nicht erstellt haben.

2. Öffnen Sie ein Komponentendiagramm, Anwendungsfalldiagramm oder UML-Klassendiagramm.

3. Öffnen Sie die Eigenschaften des Diagramms. Klicken Sie mit der rechten Maustaste auf einen leeren Bereich des Diagramms, und klicken Sie dann auf **Eigenschaften**.

4. Wählen Sie in der Eigenschaft **verknüpftes Paket** das Paket aus, das den Inhalt des Diagramms enthalten soll.

5. Erstellen Sie neue Elemente im Diagramm. Diese werden in das Paket eingefügt.

    - Der **qualifizierte Name** der einzelnen Elemente beginnt mit dem qualifizierten Namen des Pakets.

    - Im **UML-Modell-Explorer**wird jedes Element unter dem Paket angezeigt.

## <a name="moving-elements-into-and-out-of-packages"></a><a name="Moving"></a> Verschieben von Elementen in und aus Paketen
 Sie können ein oder mehrere Elemente in ein Paket oder aus einem Paket verschieben.

 Wenn Sie ein Paket verschieben, werden alle Elemente im Paket mit dem Paket verschoben.

#### <a name="to-move-an-element-into-or-out-of-a-package"></a>So verschieben Sie ein Element in ein Paket oder aus einem Paket

- Ziehen Sie im UML-Modell-Explorer das Element in die Struktur oder aus der Struktur, deren Stamm das Paket ist.

     Der qualifizierte Name des Elements wird geändert, um den Namen des neuen Pakets oder Modells anzugeben, das Besitzer des Modells ist.

     \- oder -

- Ziehen Sie in einem Klassendiagramm das Element in eine Paketform.

     Der qualifizierte Name des Elements wird geändert, um den Namen des neuen Pakets anzugeben, das Besitzer des Modells ist.

    > [!NOTE]
    > Wenn Sie ein Element aus einem Paket in einen leeren Teil des Diagramms ziehen, bleibt das gleiche Paket Besitzer des Elements. So können Sie ein Diagramm erstellen, in dem Elemente aus mehreren Paketen angezeigt werden, ohne die Pakete selbst anzeigen zu müssen.

## <a name="pasting-elements-into-a-package"></a><a name="Pasting"></a> Einfügen von Elementen in ein Paket
 Sie können ein Element in ein Paket einfügen. Wenn Sie eine Gruppe von zugehörigen Elementen in ein Paket einfügen, werden die Beziehungen zwischen ihnen ebenfalls eingefügt.

#### <a name="to-paste-elements-into-a-package-on-a-uml-class-diagram"></a>So fügen Sie in einem UML-Klassendiagramm Elemente in ein Paket ein

1. Wählen Sie in einem UML-Klassendiagramm alle Elemente aus, die Sie kopieren möchten. Klicken Sie mit der rechten Maustaste darauf, und klicken Sie dann auf **Kopieren**.

2. Klicken Sie mit der rechten Maustaste auf das Paket und dann auf **Einfügen**.

    > [!NOTE]
    > Das Paket kann in einem anderen Diagramm enthalten sein.

## <a name="import-relationships-between-packages"></a><a name="Import"></a> Importieren von Beziehungen zwischen Paketen
 Mithilfe des **Import** Tools können Sie eine Import Beziehung zwischen Paketen definieren.

 Bei einer Importbeziehung sind die im importierten Paket definierten Elemente, d. h. die Elemente am Pfeilende der Beziehung, auch im Paket definiert, aus dem der Import erfolgt. Alle Elemente, deren Sichtbarkeit als **Package** definiert ist, werden auch im importierten Paket angezeigt.

 Erstellen Sie in Importbeziehungen keine Schleifen.

## <a name="references-from-one-namespace-to-another"></a><a name="References"></a> Verweise von einem Namespace auf einen anderen
 Wenn Sie von einem Element in einem Paket auf ein Element eines anderen Pakets verweisen möchten, müssen Sie den qualifizierten Namen des Elements verwenden.

 Angenommen, das Paket `SalesCommon` definiert den Typ `CustomerAddress`. In einem anderen Paket mit dem Namen `RestaurantSales` möchten Sie den Typ `MealOrder` definieren, der über ein Attribut vom Typ „Customer Address“ verfügt. Sie haben zwei Möglichkeiten:

- Geben Sie den Typ des Attributs mit dem vollqualifizierten Namen `SalesCommon::CustomerAddress` an. Dies ist nur möglich `CustomerAddress` , wenn die **Visibility** -Eigenschaft auf **Public**festgelegt ist.

- Erstellen Sie eine Importbeziehung vom Paket `RestaurantSales` zum Paket `SalesCommon`. Dann können Sie `CustomerAddress` ohne qualifizierten Namen verwenden.

## <a name="properties-of-packages"></a><a name="Properties"></a> Eigenschaften von Paketen
 Jedes Paket verfügt über die folgenden Eigenschaften. Um die Eigenschaften anzuzeigen, klicken Sie mit der rechten Maustaste auf das Paket, entweder in einem Diagramm oder im UML-Modell-Explorer, und klicken Sie dann auf **Eigenschaften**.

|Eigenschaft|Standardwert|Beschreibung|
|--------------|-------------------|-----------------|
|**Name**|(ein neuer Name)|Der Paketname. Sie können den Namen im Diagramm oder im Eigenschaftenfenster ändern.|
|**Qualifizierter Name**|*Container* :: *Paketname*|Der vollständige Name, dem der Name des Pakets oder Modells vorangestellt ist, das das Paket enthält. Weitere Informationen finden Sie unter [Namespaces](#Namespaces).|
|**Profiles**|(leer)|Eine Liste der mit dem Paket verknüpften Profile. Diese Profile stellen Stereotype bereit, die auf Elemente im Paket angewendet werden können. Weitere Informationen finden Sie unter [Anpassen des Modells mit Profilen und Stereotypen](../modeling/customize-your-model-with-profiles-and-stereotypes.md).|
|**Sichtbarkeit**|**Öffentlich**|Die Sichtbarkeit des Pakets außerhalb des übergeordneten Pakets.|
|**Arbeitselemente**|(leer)|Eine Liste verknüpfter Arbeitselemente. Weitere Informationen finden Sie unter [Verknüpfen von Modellelementen und Arbeits Elementen](../modeling/link-model-elements-and-work-items.md).|
|**Definitions Speicherort**|(ein Name)|Der Name der Datei, in der die Informationen zum Paket gespeichert werden. Die Dateien befinden sich im Projektordner **Model Definition** . Diese Informationen können für die Quellcodeverwaltung hilfreich sein.|
|**Beschreibung**|(leer)|Eine Beschreibung des Pakets.|
|**Typi**|(leer)|Auf das Paket angewendete Stereotype. Die Liste der verfügbaren Stereotype wird von den Profilen bestimmt, die Sie für dieses Paket und die Pakete ausgewählt haben, die es enthalten. Weitere Informationen finden Sie unter [Anpassen des Modells mit Profilen und Stereotypen](../modeling/customize-your-model-with-profiles-and-stereotypes.md).|

## <a name="how-packages-are-stored"></a>Speichern von Paketen
 Wenn Sie ein neues Paket erstellen, wird eine neue **UML** -Datei im **ModelDefinition** -Projektordner erstellt. Das Stamm Modell, das auch ein Paket ist, wird ebenfalls in einer **UML** -Datei gespeichert.

 Außerdem wird jedes Diagramm in zwei Dateien gespeichert, eine, die die Formen des Diagramms darstellt, und eine **Layoutdatei** , die die Positionen der Formen aufzeichnet.

## <a name="see-also"></a>Weitere Informationen
 [Bearbeiten von UML-Modellen und-Diagrammen UML-](../modeling/edit-uml-models-and-diagrams.md) [Klassendiagramme: Referenz](../modeling/uml-class-diagrams-reference.md) [UML-Klassendiagramme: Richtlinien](../modeling/uml-class-diagrams-guidelines.md) [Verwalten von Modellen und Diagrammen unter Versionskontrolle](../modeling/manage-models-and-diagrams-under-version-control.md)
