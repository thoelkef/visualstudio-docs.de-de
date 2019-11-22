---
title: Add stereotypes to UML model elements | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, stereotypes
ms.assetid: 82545252-83ce-4e11-a419-61373be75d16
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 67d489b1446e7205d72b53e160a8c7ca87f216d7
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74292334"
---
# <a name="add-stereotypes-to-uml-model-elements"></a>Hinzufügen von Stereotypen zu UML-Modellelementen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können einem UML-Modellelement einen Stereotypen hinzufügen, um es zu kommentieren und spezielle Eigenschaften bereitzustellen. Um einem Modellelement einen Stereotypen hinzuzufügen, muss der Stereotyp in einem Profil definiert werden, und Sie müssen das Profil mit einem Paket oder dem Modell verknüpfen, das das Modellelement enthält. Jeder Stereotyp kann nur bestimmten Arten von Modellelementen hinzugefügt werden, z. B. UML-Klassen, Anwendungsfällen oder Komponenten.

 Wenn Sie beispielsweise eine UML-Klasse mit dem Stereotyp «Specification» definieren möchten, müssen Sie ihn in einem Paket oder einem Modell erstellen, das mit dem Standardprofil L2 verknüpft ist.

 Standardmäßig ist jedes Modell mit den UML-Standardprofilen L2 und L3 verknüpft.

### <a name="to-link-a-profile-to-a-model-or-a-package"></a>So verknüpfen Sie ein Profil mit einem Modell oder einem Paket

1. Open **UML Model Explorer**. On the **Architecture** menu, point to **Windows**, and then click **UML Model Explorer**.

2. Suchen Sie ein Paket oder ein Modell, das alle Elemente enthält, auf die Sie den Stereotypen im Profil anwenden möchten.

3. Right-click the package or the model and then click **Properties**.

4. In the **Properties** window, set the **Profiles** property to the profiles that contain the stereotypes you want to use.

     Die Stereotypen des Profils sind nun für alle Elemente im Modell oder Paket verfügbar. Wenn das Paket andere Pakete enthält, sind die Stereotypen ebenfalls in den darin enthaltenen Elementen verfügbar.

### <a name="to-add-stereotypes-to-model-elements-or-relationships"></a>Hinzufügen von Stereotypen zu Modellelementen oder Beziehungen

1. Right-click the model element or relationship, either on a diagram or in **UML Model Explorer**, and then click **Properties**.

    > [!NOTE]
    > Um mehreren Elementen die gleichen Stereotypen hinzuzufügen, können Sie mehrere Elemente auswählen und dann mit der rechten Maustaste aus eines davon klicken.

2. Click the **Stereotypes** property and select the stereotypes that you want to apply.

     Die ausgewählten Stereotypen werden für die meisten Arten von Elementen und Beziehungen im Modellelement in Chevrons (« ») angezeigt.

    > [!NOTE]
    > If you cannot see the **Stereotypes** property, or if the stereotype you want does not appear, verify that the model element is inside a package or a model to which the appropriate profile has been linked.

3. Einige Stereotype ermöglichen es Ihnen, die Werte zusätzlicher Eigenschaften für das Modellelement festzulegen. To see these properties, expand the **Stereotypes** property.

### <a name="to-create-model-elements-within-a-package"></a>Erstellen von Modellelementen in einem Paket

1. Create a package either in a UML Class Diagram, or in **UML Model Explorer**.

2. Fügen Sie Modellelemente für das Paket folgendermaßen hinzu:

    - Klicken Sie in einem UML-Klassendiagramm auf das Tool für ein Element, und klicken Sie dann in das Paket des Diagramms.

         \- oder -

    - In UML Model Explorer, right-click the package, point to **Add**, and then click an element type.

         \- oder -

    - Ziehen Sie im UML-Modell-Explorer ein vorhandenes Element in das Paket.

         \- oder -

    - Verknüpfen Sie ein Diagramm mit dem Paket, und erstellen Sie dann Elemente innerhalb des Diagramms.

         To do this, right-click a blank part of the diagram and then click **Properties**. In the **Properties** window, set **Linked Package** to the package you want.

         Alle neuen Elemente, die Sie im Diagramm erstellen, werden in diesem Paket definiert.

         Sie können dieses Verfahren nur für einige Typen von Diagrammen tun.

## <a name="see-also"></a>Siehe auch
 [Define a profile to extend UML](../modeling/define-a-profile-to-extend-uml.md) [Customize your model with profiles and stereotypes](../modeling/customize-your-model-with-profiles-and-stereotypes.md) [Define packages and namespaces](../modeling/define-packages-and-namespaces.md)

