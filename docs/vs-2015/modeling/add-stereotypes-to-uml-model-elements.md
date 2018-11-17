---
title: Hinzufügen von Stereotypen zu UML-Modellelementen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML model, stereotypes
ms.assetid: 82545252-83ce-4e11-a419-61373be75d16
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: dbd5f4288833a29bdfef2df97ee71ac765ae168f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51725371"
---
# <a name="add-stereotypes-to-uml-model-elements"></a>Hinzufügen von Stereotypen zu UML-Modellelementen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können einem UML-Modellelement einen Stereotypen hinzufügen, um es zu kommentieren und spezielle Eigenschaften bereitzustellen.  Um einem Modellelement einen Stereotypen hinzuzufügen, muss der Stereotyp in einem Profil definiert werden, und Sie müssen das Profil mit einem Paket oder dem Modell verknüpfen, das das Modellelement enthält. Jeder Stereotyp kann nur bestimmten Arten von Modellelementen hinzugefügt werden, z. B. UML-Klassen, Anwendungsfällen oder Komponenten.  
  
 Wenn Sie beispielsweise eine UML-Klasse mit dem Stereotyp «Specification» definieren möchten, müssen Sie ihn in einem Paket oder einem Modell erstellen, das mit dem Standardprofil L2 verknüpft ist.  
  
 Standardmäßig ist jedes Modell mit den UML-Standardprofilen L2 und L3 verknüpft.  
  
### <a name="to-link-a-profile-to-a-model-or-a-package"></a>So verknüpfen Sie ein Profil mit einem Modell oder einem Paket  
  
1.  Open **UML-Modell-Explorer**. Auf der **Architektur** Startmenü **Windows**, und klicken Sie dann auf **UML-Modell-Explorer**.  
  
2.  Suchen Sie ein Paket oder ein Modell, das alle Elemente enthält, auf die Sie den Stereotypen im Profil anwenden möchten.  
  
3.  Mit der rechten Maustaste das Paket oder das Modell, und klicken Sie dann auf **Eigenschaften**.  
  
4.  In der **Eigenschaften** legen die **Profile** Eigenschaft, um die Profile, die die Stereotype enthalten, Sie verwenden möchten.  
  
     Die Stereotypen des Profils sind nun für alle Elemente im Modell oder Paket verfügbar. Wenn das Paket andere Pakete enthält, sind die Stereotypen ebenfalls in den darin enthaltenen Elementen verfügbar.  
  
### <a name="to-add-stereotypes-to-model-elements-or-relationships"></a>Hinzufügen von Stereotypen zu Modellelementen oder Beziehungen  
  
1.  Mit der rechten Maustaste das Modellelement oder die Beziehung, in einem Diagramm oder im **UML-Modell-Explorer**, und klicken Sie dann auf **Eigenschaften**.  
  
    > [!NOTE]
    >  Um mehreren Elementen die gleichen Stereotypen hinzuzufügen, können Sie mehrere Elemente auswählen und dann mit der rechten Maustaste aus eines davon klicken.  
  
2.  Klicken Sie auf die **Stereotype** Eigenschaft, und wählen Sie die Stereotype, die Sie anwenden möchten.  
  
     Die ausgewählten Stereotypen werden für die meisten Arten von Elementen und Beziehungen im Modellelement in Chevrons (« ») angezeigt.  
  
    > [!NOTE]
    >  Wenn Sie nicht sehen können die **Stereotype** -Eigenschaft, oder wenn das gewünschte Stereotyp nicht angezeigt wird, stellen Sie sicher, dass das Modellelement in einem Paket oder ein Modell ist, das entsprechende Profil verknüpft wurde.  
  
3.  Einige Stereotype ermöglichen es Ihnen, die Werte zusätzlicher Eigenschaften für das Modellelement festzulegen. Um diese Eigenschaften anzuzeigen, erweitern Sie die **Stereotype** Eigenschaft.  
  
### <a name="to-create-model-elements-within-a-package"></a>Erstellen von Modellelementen in einem Paket  
  
1.  Erstellen Sie ein Paket aus, entweder in einem UML-Klassendiagramm oder im **UML-Modell-Explorer**.  
  
2.  Fügen Sie Modellelemente für das Paket folgendermaßen hinzu:  
  
    -   Klicken Sie in einem UML-Klassendiagramm auf das Tool für ein Element, und klicken Sie dann in das Paket des Diagramms.  
  
         \- oder –  
  
    -   Im UML-Modell-Explorer mit der Maustaste des Pakets, zeigen Sie auf **hinzufügen**, und klicken Sie dann auf einen Elementtyp.  
  
         \- oder –  
  
    -   Ziehen Sie im UML-Modell-Explorer ein vorhandenes Element in das Paket.  
  
         \- oder –  
  
    -   Verknüpfen Sie ein Diagramm mit dem Paket, und erstellen Sie dann Elemente innerhalb des Diagramms.  
  
         Zu diesem Zweck mit der rechten Maustaste in eines leeren Bereich des Diagramms, und klicken Sie dann auf **Eigenschaften**. In der **Eigenschaften** legen **Linked Package** auf das gewünschte Paket.  
  
         Alle neuen Elemente, die Sie im Diagramm erstellen, werden in diesem Paket definiert.  
  
         Sie können dieses Verfahren nur für einige Typen von Diagrammen tun.  
  
## <a name="see-also"></a>Siehe auch  
 [Definieren eines Profils zum Erweitern von UML](../modeling/define-a-profile-to-extend-uml.md)   
 [Anpassen des Modells mit Profilen und Stereotypen](../modeling/customize-your-model-with-profiles-and-stereotypes.md)   
 [Definieren von Paketen und namespaces](../modeling/define-packages-and-namespaces.md)   
 [Color UML-Klassen nach Stereotyp](http://code.msdn.microsoft.com/UML-Color-Classes-by-07de2b70)



