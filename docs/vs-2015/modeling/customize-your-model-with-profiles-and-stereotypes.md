---
title: Anpassen des Modells mit Profilen und Stereotypen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML model, profiles
- UML model, stereotypes
- UML model, customizing
ms.assetid: fd607157-0d3a-4583-a84e-427a4b2a5acb
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 33e887764c535083c2449a7d333868b2ccd9c4c5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51727708"
---
# <a name="customize-your-model-with-profiles-and-stereotypes"></a>Anpassen des Modells mit Profilen und Stereotypen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio können Sie die standardmäßigen UML-Modellelemente wie z. B. Klassen und Komponenten an spezifische Zwecke anpassen. Sie können anwenden, eine *Stereotyp* zu einem Modellelement, die das Element der Liste der Eigenschaften ändern können. Stereotype werden in Auflistungen namens definiert *Profile*.  
  
 Welche Versionen von Visual Studio dieses Feature unterstützen, erfahren Sie unter [Versionsunterstützung für Architektur- und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Um ein Stereotyp zu verwenden, verknüpfen Sie ein Paket mit einem Profil. So können Sie die im Profil definierten Stereotype auf die Elemente im Paket anwenden. Einige Profile werden zusammen mit Visual Studio installiert. Darüber hinaus können Sie eigene Profile definieren.  
  
 Stereotype können in der Eigenschaftenliste eines Elements festgelegt werden. Für die wichtigsten Arten von Formen in einem Diagramm werden die angewendeten Stereotype auch in der Form angezeigt, wie im Beispiel dargestellt.  
  
 ![Ein UML-Klasse mit Stereotyp. ](../modeling/media/uml-class-stereotype.png "UML_class_stereotype")  
  
> [!NOTE]
>  Wenn Sie ein Modell mithilfe eines Profils erstellen und dann das Modell für einen anderen Benutzer freigeben, werden für diesen die Stereotype nur angezeigt, wenn auf dem Computer des Benutzers das gleiche Profil installiert ist.  
  
## <a name="related-topics"></a>Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[Hinzufügen von Stereotypen zu UML-Modellelementen](../modeling/add-stereotypes-to-uml-model-elements.md)|Einfügen eines Modellelements in ein Paket, Verknüpfen des Pakets mit einem Profil und Anwenden eines Stereotyps auf das Element|  
|[Standardstereotypenfür UML-Modelle](../modeling/standard-stereotypes-for-uml-models.md)|Die UML-Standardprofile L2 und L3 werden zusammen mit Visual Studio installiert, und jedes Modell wird standardmäßig mit ihnen verknüpft. Sie stellen Stereotype bereit, mit denen Sie Modelle kommentieren können.<br /><br /> Sie können z. B. das Stereotyp „specification“ auf eine Klasse anwenden, um anzugeben, dass ihr einziger Zweck darin besteht, das extern sichtbare Verhalten ihrer Instanzen zu definieren.|  
|[Definieren eines Profils zum Erweitern von UML](../modeling/define-a-profile-to-extend-uml.md)|Sie können eigene Stereotype und Tools definieren, die an Ihren Anwendungsbereich angepasst sind.<br /><br /> Wenn Sie z. B. Banksoftware entwickeln, können Sie das Stereotyp „Account“ definieren, das auf Klassen angewendet werden kann. Anschließend können Sie Klassendiagramme verwenden, um andere Typen von Konten und ihre Beziehungen zu beschreiben.|  
|[Installieren eines UML-Profils](../modeling/install-a-uml-profile.md)|Wenn Sie ein UML-Profil von einem anderen Benutzer erhalten haben, können Sie es auf Ihrem Computer installieren.|  
|[Definieren eines benutzerdefinierten Elements für die Modellerstellungstoolbox](../modeling/define-a-custom-modeling-toolbox-item.md)|Ein benutzerdefiniertes Toolboxelement erspart Ihnen das wiederholte Festlegen eines Stereotyps für neue Elemente.|  
|[Color UML-Klassen nach Stereotyp](http://code.msdn.microsoft.com/UML-Color-Classes-by-07de2b70)|Mit diesem Beispielcode werden die UML-Diagramme erweitert. Die Farbe einer UML-Form wird automatisch entsprechend dem Stereotyp des Elements festgelegt.|



