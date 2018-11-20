---
title: Definieren von Paketen und Namespaces | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML model, namespaces
- UML, namespaces
- UML, packages
- UML model, packages
ms.assetid: 79147068-02d5-4b70-933d-f647c1da3829
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: b9295b5af83270069df11e6460ee85dfe0fd9c73
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51741910"
---
# <a name="define-packages-and-namespaces"></a>Definieren von Paketen und Namespaces
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio eine *Paket* ist ein Container für die Definitionen von UML-Elementen wie z. B. Klassen, Anwendungsfälle und Komponenten. Ein Paket kann auch andere Pakete enthalten.  
  
 Im UML-Modell-Explorer werden alle Definitionen in einem Paket unter dem Paket geschachtelt. Das UML-Modell ist eine Art von Paket und bildet den Stamm der Struktur.  
  
 Welche Versionen von Visual Studio dieses Feature unterstützen, erfahren Sie unter [Versionsunterstützung für Architektur- und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="in-this-topic"></a>In diesem Thema  
 [Namespaces](#Namespaces)  
  
 [Erstellen und Anzeigen von Paketen](#Packages)  
  
 [Erstellen von Modellelementen in Paketen](#Elements)  
  
 [Verschieben von Elementen in oder aus einem Paket](#Moving)  
  
 [Einfügen von Elementen in einem Paket](#Pasting)  
  
 [Importbeziehungen zwischen Paketen](#Import)  
  
 [Verweise aus einem Namespace in eine andere](#References)  
  
 [Eigenschaften von Paketen](#Properties)  
  
##  <a name="Namespaces"></a> Namespaces  
 Mit Paketen lässt sich Arbeit in unterschiedliche Bereiche aufteilen. Jedes Paket definiert einen Namespace, damit keine Konflikte zwischen Namen auftreten, die in anderen Paketen definiert sind.  
  
 Die Eigenschaft für den qualifizierten Namen jedes Elements ist der qualifizierte Name des Pakets, zu dem es gehört, gefolgt vom eigenen Namen des Elements. Wenn der Name des Pakets `MyPackage` lautet, lautet der qualifizierte Name einer Klasse in dem Paket beispielsweise `MyPackage::MyClass`. Da jedes Element in einem Modell enthalten ist, beginnt jeder qualifizierte Name mit dem Namen des Modells.  
  
 Ein Modell definiert auch einen Namespace, sodass der qualifizierte Name jedes Elements in einem Modell mit dem Namen des Modells beginnt.  
  
 Andere Modellelemente definieren ebenfalls Namespaces. Beispielsweise gehört ein Vorgang zu dem von der übergeordneten Klasse des Vorgangs definierten Namespace, sodass sein qualifizierter Name etwa `MyModel ::MyPackage ::MyClass ::MyOperation` lautet. Entsprechend gehört eine Aktion zu dem Namespace, der von der übergeordneten Aktivität der Aktion definiert wird.  
  
 Pakete sind Container. Wenn Sie ein Paket verschieben oder löschen, werden die Klassen, Pakete und andere im Paket definierten Elemente ebenfalls verschoben bzw. gelöscht. Das Gleiche gilt für andere Elemente, die Namespaces definieren.  
  
##  <a name="Packages"></a> Erstellen und Anzeigen von Paketen  
 Sie können ein Paket in einem UML-Klassendiagramm oder im UML-Modell-Explorer erstellen.  
  
#### <a name="to-create-a-package-in-a-uml-class-diagram"></a>So erstellen Sie ein Paket in einem UML-Klassendiagramm  
  
1.  Öffnen Sie ein UML-Klassendiagramm, oder erstellen Sie ein neues UML-Klassendiagramm.  
  
2.  Klicken Sie auf die **Paket** Tool.  
  
3.  Klicken Sie auf eine beliebige Stelle im Diagramm. Eine neue Paketform wird angezeigt.  
  
     Sie können in ein vorhandenes Paket klicken, um ein Paket in einem anderen Paket zu schachteln.  
  
4.  Geben Sie einen neuen Namen für das Paket ein.  
  
#### <a name="to-create-a-package-in-uml-model-explorer"></a>So erstellen Sie ein Paket im UML-Modell-Explorer  
  
1. Open **UML-Modell-Explorer**. Auf der **Architektur** Startmenü **Windows**, und klicken Sie dann auf die **UML-Modell-Explorer**.  
  
2. Klicken Sie mit der rechten Maustaste auf ein Paket oder Modell, dem Sie ein neues Paket hinzufügen möchten.  
  
   > [!NOTE]
   >  Sie können ein Paket in einem anderen Paket schachteln.  
  
3. Zeigen Sie auf **hinzufügen** , und klicken Sie dann auf **Paket**.  
  
    Im Modell wird ein neues Paket angezeigt.  
  
4. Geben Sie einen neuen Namen für das Paket ein.  
  
   Wenn Sie im UML-Modell-Explorer ein Paket erstellt haben, können Sie es in einem UML-Klassendiagramm anzeigen. Sie können ein Paket auch in mehreren UML-Klassendiagrammen anzeigen.  
  
#### <a name="to-show-an-existing-package-on-a-uml-class-diagram"></a>So zeigen Sie ein vorhandenes Paket in einem UML-Klassendiagramm an  
  
-   Ziehen Sie das Paket aus dem UML-Modell-Explorer in das Klassendiagramm.  
  
    > [!NOTE]
    >  Hierdurch wird in diesem Diagramm eine Ansicht des Pakets erstellt. In der Ansicht werden nicht unbedingt alle im Paket enthaltenen Elemente angezeigt. Um sicherzustellen, dass der gesamte Inhalt eines Pakets angezeigt wird, zeigen Sie das Paket im UML-Modell-Explorer an.  
  
##  <a name="Elements"></a> Erstellen von Modellelementen in Paketen  
 Es gibt vier Verfahren, mit denen Sie Modellelemente in ein Paket einfügen können:  
  
- Fügen Sie im UML-Modell-Explorer einem Paket ein neues Element hinzu.  
  
- Fügen Sie in einem UML-Klassendiagramm Paketen Klassen und andere Typen hinzu.  
  
- Legen Sie die **LinkedPackage** -Eigenschaft eines Diagramms, damit neue Elemente im Diagramm erstellt werden innerhalb der von Ihnen angegebene Paket platziert. Klassendiagramme, Komponentendiagramme und Anwendungsfalldiagramme können auf diese Weise mit einem Paket verknüpft werden.  
  
- Verschieben Sie im UML-Modell-Explorer Elemente in ein Paket oder aus einem Paket.  
  
  Im UML-Modell-Explorer wird ein Element in einem Paket unter dem Paket angezeigt, und sein qualifizierter Name beginnt mit dem qualifizierten Namen des Pakets. Klicken Sie zum Anzeigen der qualifizierte Name eines Elements mit der rechten Maustaste in des Elements, und klicken Sie dann auf **Eigenschaften**. Die **qualifizierten Namen** Eigenschaft angezeigt wird, der **Eigenschaften** Fenster.  
  
#### <a name="to-create-an-element-in-a-package-in-uml-model-explorer"></a>So erstellen Sie im UML-Modell-Explorer ein Element in einem Paket  
  
1.  Open **UML-Modell-Explorer**. Auf der **Ansicht** Startmenü **andere Windows**, und klicken Sie dann auf **UML-Modell-Explorer**.  
  
2.  Klicken Sie mit der rechten Maustaste auf ein Paket oder Modell, dem Sie ein neues Element hinzufügen möchten.  
  
3.  Zeigen Sie auf **hinzufügen**, und klicken Sie dann auf die Art des Elements, das Sie hinzufügen möchten.  
  
     Das neue Element wird unter dem Paket angezeigt.  
  
4.  Geben Sie einen Namen für das neue Element ein.  
  
    > [!NOTE]
    >  Das neue Element wird in keinem Diagramm angezeigt. Um eine Ansicht des neuen Elements zu erstellen, können Sie es aus dem UML-Modell-Explorer in ein Diagramm ziehen. Das Diagramm muss von einem Diagrammtyp sein, in dem diese Art von Element angezeigt wird.  
  
#### <a name="to-create-an-element-in-a-package-on-a-uml-class-diagram"></a>So erstellen Sie in einem UML-Klassendiagramm ein Element in einem Paket  
  
1.  Öffnen Sie ein Klassendiagramm, in dem das Paket angezeigt wird.  
  
    -   Erstellen Sie ein neues Paket, sofern Sie noch kein neues Paket erstellt haben.  
  
    -   Damit wird ein vorhandenes Paket in einem Klassendiagramm angezeigt werden, können Sie das Paket von ziehen **UML-Modell-Explorer** in das Klassendiagramm.  
  
2.  Klicken Sie auf das Tool für eine Klasse, eine Schnittstelle, eine Enumeration oder ein Paket.  
  
3.  Klicken Sie auf das Paket, in das Sie das neue Element einfügen möchten.  
  
     Das neue Element wird in dem Paket angezeigt.  
  
#### <a name="to-create-all-the-elements-of-a-diagram-in-a-specified-package"></a>So erstellen Sie alle Elemente eines Diagramms in einem angegebenen Paket  
  
1.  Erstellen Sie das Paket, sofern Sie es noch nicht erstellt haben.  
  
2.  Öffnen Sie ein Komponentendiagramm, Anwendungsfalldiagramm oder UML-Klassendiagramm.  
  
3.  Öffnen Sie die Eigenschaften des Diagramms. Mit der rechten Maustaste in einen leeren Bereich des Diagramms, und klicken Sie dann auf **Eigenschaften**.  
  
4.  In der **Linked Package** -Eigenschaft, wählen Sie das Paket, das die den Inhalt des Diagramms enthalten soll.  
  
5.  Erstellen Sie neue Elemente im Diagramm. Diese werden in das Paket eingefügt.  
  
    -   Die **qualifizierten Namen** jedes Elements beginnt mit dem qualifizierten Namen des Pakets.  
  
    -   In **UML-Modell-Explorer**, jedes Element wird unter dem Paket angezeigt.  
  
##  <a name="Moving"></a> Verschieben von Elementen in und aus Paketen  
 Sie können ein oder mehrere Elemente in ein Paket oder aus einem Paket verschieben.  
  
 Wenn Sie ein Paket verschieben, werden alle Elemente im Paket mit dem Paket verschoben.  
  
#### <a name="to-move-an-element-into-or-out-of-a-package"></a>So verschieben Sie ein Element in ein Paket oder aus einem Paket  
  
-   Ziehen Sie im UML-Modell-Explorer das Element in die Struktur oder aus der Struktur, deren Stamm das Paket ist.  
  
     Der qualifizierte Name des Elements wird geändert, um den Namen des neuen Pakets oder Modells anzugeben, das Besitzer des Modells ist.  
  
     \- oder –  
  
-   Ziehen Sie in einem Klassendiagramm das Element in eine Paketform.  
  
     Der qualifizierte Name des Elements wird geändert, um den Namen des neuen Pakets anzugeben, das Besitzer des Modells ist.  
  
    > [!NOTE]
    >  Wenn Sie ein Element aus einem Paket in einen leeren Teil des Diagramms ziehen, bleibt das gleiche Paket Besitzer des Elements. So können Sie ein Diagramm erstellen, in dem Elemente aus mehreren Paketen angezeigt werden, ohne die Pakete selbst anzeigen zu müssen.  
  
##  <a name="Pasting"></a> Einfügen von Elementen in einem Paket  
 Sie können ein Element in ein Paket einfügen. Wenn Sie eine Gruppe von zugehörigen Elementen in ein Paket einfügen, werden die Beziehungen zwischen ihnen ebenfalls eingefügt.  
  
#### <a name="to-paste-elements-into-a-package-on-a-uml-class-diagram"></a>So fügen Sie in einem UML-Klassendiagramm Elemente in ein Paket ein  
  
1.  Wählen Sie in einem UML-Klassendiagramm alle Elemente aus, die Sie kopieren möchten. Mit der rechten Maustaste eine davon aus, und klicken Sie dann auf **Kopie**.  
  
2.  Mit der rechten Maustaste in des Pakets, und klicken Sie dann auf **einfügen**.  
  
    > [!NOTE]
    >  Das Paket kann in einem anderen Diagramm enthalten sein.  
  
##  <a name="Import"></a> Importbeziehungen zwischen Paketen  
 Sie können eine importbeziehung zwischen Paketen mit definieren die **importieren** Tool.  
  
 Bei einer Importbeziehung sind die im importierten Paket definierten Elemente, d. h. die Elemente am Pfeilende der Beziehung, auch im Paket definiert, aus dem der Import erfolgt. Elemente, deren Sichtbarkeit als definiert ist **Paket** werden auch in der importierenden Pakets angezeigt.  
  
 Erstellen Sie in Importbeziehungen keine Schleifen.  
  
##  <a name="References"></a> Verweise aus einem Namespace in eine andere  
 Wenn Sie von einem Element in einem Paket auf ein Element eines anderen Pakets verweisen möchten, müssen Sie den qualifizierten Namen des Elements verwenden.  
  
 Angenommen, das Paket `SalesCommon` definiert den Typ `CustomerAddress`. In einem anderen Paket mit dem Namen `RestaurantSales` möchten Sie den Typ `MealOrder` definieren, der über ein Attribut vom Typ „Customer Address“ verfügt. Sie verfügen über zwei Möglichkeiten:  
  
-   Geben Sie den Typ des Attributs mit dem vollqualifizierten Namen `SalesCommon::CustomerAddress` an. Gehen Sie so nur vor, wenn `CustomerAddress` hat seine **Sichtbarkeit** -Eigenschaftensatz auf **öffentliche**.  
  
-   Erstellen Sie eine Importbeziehung vom Paket `RestaurantSales` zum Paket `SalesCommon`. Dann können Sie `CustomerAddress` ohne qualifizierten Namen verwenden.  
  
##  <a name="Properties"></a> Eigenschaften von Paketen  
 Jedes Paket verfügt über die folgenden Eigenschaften. Klicken Sie zum Anzeigen der Eigenschaften, mit der rechten Maustaste in des Pakets in einem Diagramm oder im UML-Modell-Explorer, und klicken Sie dann auf **Eigenschaften**.  
  
|Eigenschaft|Standardwert|Beschreibung|  
|--------------|-------------------|-----------------|  
|**Name**|(ein neuer Name)|Der Paketname. Sie können den Namen im Diagramm oder im Eigenschaftenfenster ändern.|  
|**Qualifizierter Name**|*Container* :: *Paketname*|Der vollständige Name, dem der Name des Pakets oder Modells vorangestellt ist, das das Paket enthält. Weitere Informationen finden Sie unter [Namespaces](#Namespaces).|  
|**Profile**|(leer)|Eine Liste der mit dem Paket verknüpften Profile. Diese Profile stellen Stereotype bereit, die auf Elemente im Paket angewendet werden können. Weitere Informationen finden Sie unter [Anpassen des Modells mit Profilen und Stereotypen](../modeling/customize-your-model-with-profiles-and-stereotypes.md).|  
|**Sichtbarkeit**|**Public**|Die Sichtbarkeit des Pakets außerhalb des übergeordneten Pakets.|  
|**Typen von Arbeitselementen**|(leer)|Eine Liste verknüpfter Arbeitsaufgaben. Weitere Informationen finden Sie unter [Verknüpfen von Modellelementen und Arbeitsaufgaben](../modeling/link-model-elements-and-work-items.md).|  
|**Speicherort der Definition**|(ein Name)|Der Name der Datei, in der die Informationen zum Paket gespeichert werden. Die Dateien befinden sich die **ModelDefinition** Projektordner. Diese Informationen können für die Quellcodeverwaltung hilfreich sein.|  
|**Beschreibung**|(leer)|Eine Beschreibung des Pakets.|  
|**Stereotype**|(leer)|Auf das Paket angewendete Stereotype. Die Liste der verfügbaren Stereotype wird von den Profilen bestimmt, die Sie für dieses Paket und die Pakete ausgewählt haben, die es enthalten. Weitere Informationen finden Sie unter [Anpassen des Modells mit Profilen und Stereotypen](../modeling/customize-your-model-with-profiles-and-stereotypes.md).|  
  
## <a name="how-packages-are-stored"></a>Speichern von Paketen  
 Wenn Sie ein neues Paket erstellen ein neues **.uml** Datei wird erstellt, der **ModelDefinition** Projektordner. Das Stammmodell, das auch ein Paket ist, befindet sich auch in einem **.uml** Datei.  
  
 Darüber hinaus befindet sich jedes Diagramm in zwei Dateien, die im Diagramm enthaltenen Formen, darstellt und einen **.layout** -Datei, die sich die Positionen der Formen zeichnet.  
  
## <a name="see-also"></a>Siehe auch  
 [Bearbeiten von UML-Modellen und-Diagrammen](../modeling/edit-uml-models-and-diagrams.md)   
 [UML-Klassendiagramme: Referenz](../modeling/uml-class-diagrams-reference.md)   
 [UML-Klassendiagramme: Richtlinien](../modeling/uml-class-diagrams-guidelines.md)   
 [Verwalten von Modellen und Diagrammen unter Versionskontrolle](../modeling/manage-models-and-diagrams-under-version-control.md)



