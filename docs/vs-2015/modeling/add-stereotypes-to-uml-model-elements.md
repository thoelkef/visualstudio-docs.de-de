---
title: Hinzufügen von Stereotypen zu UML-Modellelementen | Microsoft-Dokumentation
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

1. Öffnet den **UML-Modell-Explorer**. Zeigen Sie im Menü **Architektur** auf **Fenster**, und klicken Sie dann auf UML- **Modell-Explorer**.

2. Suchen Sie ein Paket oder ein Modell, das alle Elemente enthält, auf die Sie den Stereotypen im Profil anwenden möchten.

3. Klicken Sie mit der rechten Maustaste auf das Paket oder Modell, und klicken Sie dann auf **Eigenschaften**.

4. Legen Sie im Fenster **Eigenschaften** die Eigenschaft **profile** auf die Profile fest, die die stereotype enthalten, die Sie verwenden möchten.

     Die Stereotypen des Profils sind nun für alle Elemente im Modell oder Paket verfügbar. Wenn das Paket andere Pakete enthält, sind die Stereotypen ebenfalls in den darin enthaltenen Elementen verfügbar.

### <a name="to-add-stereotypes-to-model-elements-or-relationships"></a>Hinzufügen von Stereotypen zu Modellelementen oder Beziehungen

1. Klicken Sie mit der rechten Maustaste auf das Modellelement oder die Beziehung, entweder in einem Diagramm oder im **UML-Modell-Explorer**, und klicken Sie dann auf **Eigenschaften**.

    > [!NOTE]
    > Um mehreren Elementen die gleichen Stereotypen hinzuzufügen, können Sie mehrere Elemente auswählen und dann mit der rechten Maustaste aus eines davon klicken.

2. Klicken Sie auf die Eigenschaft **Stereotype** , und wählen Sie die stereotype aus, die Sie anwenden möchten

     Die ausgewählten Stereotypen werden für die meisten Arten von Elementen und Beziehungen im Modellelement in Chevrons (« ») angezeigt.

    > [!NOTE]
    > Wenn die Eigenschaft **Stereotype** nicht angezeigt wird oder das gewünschte Stereotyp nicht angezeigt wird, überprüfen Sie, ob sich das Modellelement innerhalb eines Pakets oder Modells befindet, mit dem das entsprechende Profil verknüpft wurde.

3. Einige Stereotype ermöglichen es Ihnen, die Werte zusätzlicher Eigenschaften für das Modellelement festzulegen. Um diese Eigenschaften anzuzeigen, erweitern Sie die Eigenschaft **Stereotype** .

### <a name="to-create-model-elements-within-a-package"></a>Erstellen von Modellelementen in einem Paket

1. Erstellen Sie ein Paket entweder in einem UML-Klassendiagramm oder im **UML-Modell-Explorer**.

2. Fügen Sie Modellelemente für das Paket folgendermaßen hinzu:

    - Klicken Sie in einem UML-Klassendiagramm auf das Tool für ein Element, und klicken Sie dann in das Paket des Diagramms.

         \- oder –

    - Klicken Sie im UML-Modell-Explorer mit der rechten Maustaste auf das Paket, zeigen Sie auf **Hinzufügen**, und klicken Sie auf einen Elementtyp.

         \- oder –

    - Ziehen Sie im UML-Modell-Explorer ein vorhandenes Element in das Paket.

         \- oder –

    - Verknüpfen Sie ein Diagramm mit dem Paket, und erstellen Sie dann Elemente innerhalb des Diagramms.

         Klicken Sie dazu mit der rechten Maustaste auf einen leeren Bereich des Diagramms, und klicken Sie dann auf **Eigenschaften**. Legen Sie im Fenster **Eigenschaften** das **verknüpfte Paket** auf das gewünschte Paket fest.

         Alle neuen Elemente, die Sie im Diagramm erstellen, werden in diesem Paket definiert.

         Sie können dieses Verfahren nur für einige Typen von Diagrammen tun.

## <a name="see-also"></a>Siehe auch
 [Definieren eines Profils zum Erweitern von UML](../modeling/define-a-profile-to-extend-uml.md) [Anpassen des Modells mit Profilen und Stereotypen definieren von](../modeling/customize-your-model-with-profiles-and-stereotypes.md) [Paketen und Namespaces](../modeling/define-packages-and-namespaces.md)

