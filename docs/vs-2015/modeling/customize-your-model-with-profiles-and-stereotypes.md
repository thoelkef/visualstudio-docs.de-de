---
title: Anpassen des Modells mit Profilen und Stereotypen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, profiles
- UML model, stereotypes
- UML model, customizing
ms.assetid: fd607157-0d3a-4583-a84e-427a4b2a5acb
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b634b11418ef2d4220dc4eb07c825b514ab5494c
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301201"
---
# <a name="customize-your-model-with-profiles-and-stereotypes"></a>Anpassen des Modells mit Profilen und Stereotypen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio können Sie die standardmäßigen UML-Modellelemente wie z. B. Klassen und Komponenten an spezifische Zwecke anpassen. Sie können ein *Stereotyp* auf ein Modellelement anwenden, das die Liste der Eigenschaften des Elements ändern kann. Stereotype werden in Auflistungen namens *profile*definiert.

 Welche Versionen von Visual Studio dieses Feature unterstützen, erfahren Sie unter [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Um ein Stereotyp zu verwenden, verknüpfen Sie ein Paket mit einem Profil. So können Sie die im Profil definierten Stereotype auf die Elemente im Paket anwenden. Einige Profile werden zusammen mit Visual Studio installiert. Darüber hinaus können Sie eigene Profile definieren.

 Stereotype können in der Eigenschaftenliste eines Elements festgelegt werden. Für die wichtigsten Arten von Formen in einem Diagramm werden die angewendeten Stereotype auch in der Form angezeigt, wie im Beispiel dargestellt.

 ![Eine UML-Klasse mit einem Stereotyp.](../modeling/media/uml-class-stereotype.png "UML_class_stereotype")

> [!NOTE]
> Wenn Sie ein Modell mithilfe eines Profils erstellen und dann das Modell für einen anderen Benutzer freigeben, werden für diesen die Stereotype nur angezeigt, wenn auf dem Computer des Benutzers das gleiche Profil installiert ist.

## <a name="related-topics"></a>Verwandte Themen

|Titel|Beschreibung|
|-----------|-----------------|
|[Hinzufügen von Stereotypen zu UML-Modellelementen](../modeling/add-stereotypes-to-uml-model-elements.md)|Einfügen eines Modellelements in ein Paket, Verknüpfen des Pakets mit einem Profil und Anwenden eines Stereotyps auf das Element|
|[Standardstereotypenfür UML-Modelle](../modeling/standard-stereotypes-for-uml-models.md)|Die UML-Standardprofile L2 und L3 werden zusammen mit Visual Studio installiert, und jedes Modell wird standardmäßig mit ihnen verknüpft. Sie stellen Stereotype bereit, mit denen Sie Modelle kommentieren können.<br /><br /> Sie können z. B. das Stereotyp „specification“ auf eine Klasse anwenden, um anzugeben, dass ihr einziger Zweck darin besteht, das extern sichtbare Verhalten ihrer Instanzen zu definieren.|
|[Definieren eines Profils zum Erweitern von UML](../modeling/define-a-profile-to-extend-uml.md)|Sie können eigene Stereotype und Tools definieren, die an Ihren Anwendungsbereich angepasst sind.<br /><br /> Wenn Sie z. B. Banksoftware entwickeln, können Sie das Stereotyp „Account“ definieren, das auf Klassen angewendet werden kann. Anschließend können Sie Klassendiagramme verwenden, um andere Typen von Konten und ihre Beziehungen zu beschreiben.|
|[Installieren eines UML-Profils](../modeling/install-a-uml-profile.md)|Wenn Sie ein UML-Profil von einem anderen Benutzer erhalten haben, können Sie es auf Ihrem Computer installieren.|
|[Definieren eines benutzerdefinierten Elements für die Modellerstellungstoolbox](../modeling/define-a-custom-modeling-toolbox-item.md)|Ein benutzerdefiniertes Toolboxelement erspart Ihnen das wiederholte Festlegen eines Stereotyps für neue Elemente.|
