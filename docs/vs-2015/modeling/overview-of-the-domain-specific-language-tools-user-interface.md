---
title: Übersicht über die DSL-Tools-Benutzeroberfläche | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.editor
helpviewer_keywords:
- Domain-Specific Language Tools, user interface
ms.assetid: 81ae6b35-6819-41d0-953b-6b4ed81f9227
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 25d8f34488c0fee954eb9ab2d372750518433f4a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47509607"
---
# <a name="overview-of-the-domain-specific-language-tools-user-interface"></a>Übersicht über die Benutzeroberfläche für domänenspezifische Sprachtools
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Überblick über die Benutzeroberfläche für domänenspezifische Sprachtools](https://docs.microsoft.com/visualstudio/modeling/overview-of-the-domain-specific-language-tools-user-interface).  
  
Beim ersten Öffnen einer Projektmappe domänenspezifische Sprachtools (DSL-Tools) in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], die Benutzeroberfläche wird in der folgende Abbildung ähneln.  
  
 ![DSL-Designers](../modeling/media/dsl-designer.png "Dsl_designer")  
  
 In der folgende Tabelle wird erläutert, wie die Teile der Benutzeroberfläche verwendet werden.  
  
|**Element**|**Definition**|  
|-----------------|--------------------|  
|Diagramm|Das Diagramm zeigt das Domänenmodell.<br /><br /> Das Diagramm verfügt über zwei Seiten. Eine Seite definiert die Typen der Elemente in Ihren Modellen. Die andere Seite definiert, wie die Modelle auf dem Bildschirm angezeigt werden.|  
|Werkzeugkasten|Ziehen Sie die Tools aus der Toolbox auf das Hinzufügen von Domänenklassen und shape-Typen im Diagramm. Um Beziehungen, Connectors und formzuordnungen hinzuzufügen, klicken Sie auf das Tool, und klicken Sie dann Quellknoten im Diagramm, und klicken Sie dann den Zielknoten.|  
|DSL-Explorer|**DSL-Explorer** wird angezeigt, wenn eine DSL-Definition des aktiven Fensters. Es zeigt die DSL als Struktur. DSL-Explorer können Sie die Features des Modells zu bearbeiten, die nicht im Diagramm angezeigt werden. Sie können z. B. Toolboxelemente hinzufügen und auf den Überprüfungsprozess wechseln, indem die **DSL-Explorer**.|  
|Fenster "DSL-Details"|Die **DSL-Details** Fenster zeigt die Eigenschaften der Domäne des Modells-Elemente, mit denen Sie steuern, wie Elemente angezeigt werden und wie die Elemente kopiert und gelöscht werden.<br /><br /> -Standardmäßig die **DSL-Details** Fenster neben dem **Fehlerliste** und **Ausgabe** Windows.|  
  
## <a name="the-domain-model-diagram"></a>Das Modelldiagramm Domäne  
 Das Modelldiagramm Domäne wird in zwei Teile unterteilt. Eine Seite des Diagramms zeigt die Elemente und Beziehungen im Modell an. Die andere Seite zeigt, wie das Modell ist, angezeigt werden, sowie die Formen, die verwendet werden, um die Elemente und die Eigenschaften des Modelldiagramms anzuzeigen. Die folgende Abbildung zeigt die Elemente des Diagramms.  
  
 ![DSL-Designer mit Swimlane](../modeling/media/dsl-desinger.png "Dsl_desinger")  
  
 In der folgende Tabelle werden einige der Elemente im Modelldiagramm Domäne erläutert.  
  
|**Begriff**|**Definition**|  
|--------------|--------------------|  
|Domänenklasse|Domänenklassen werden die Typen der Elemente in Ihren Modellen.<br /><br /> Eine Domänenklasse kann mehr als einmal in einem Diagramm angezeigt werden, ist dies das Ziel von mehr als eine Beziehung.<br /><br /> Zum Hinzufügen einer Domänenklasse ziehen Sie das Tool für die Klasse von Domänen aus der **Toolbox** auf die **Klassen und Beziehungen** Seite des Diagramms.|  
|Domänenbeziehung|Domänenbeziehungen sind die Typen von Links zwischen Elementen in Ihren Modellen.<br /><br /> Ein *einbettende Beziehung* gibt an, dass das Zielelement im Besitz der Source-Element enthalten sind und als durchgezogene Linie wird angezeigt. Jedes Element in einem Modell sollte das Ziel einer einbettenden Beziehung sein, damit, dass das Modell eine Struktur bildet. Ein *verweisbeziehung* gibt einen allgemeinen Link zwischen Modellelementen und wird als gestrichelte Linie dargestellt. Jedes Element kann eine beliebige Anzahl von Verweislinks haben.<br /><br /> Erstellen Sie eine Beziehung, indem Sie auf das Tool für die **Toolbox**, klicken Sie auf die quelldomänenklasse, und klicken Sie dann auf die Zielklasse.|  
|Formen und Konnektoren|Formen angeben wie Modellelemente in einer DSL-Diagramm. angezeigt werden soll, können Connectors Zeilen in einem DSL-Diagramm, das zum Anzeigen von Beziehungen verwendet werden kann.<br /><br /> Um eine Form oder den Connector zu erstellen, ziehen Sie das Tool die **Diagrammelemente** Seite des Diagramms.|  
|Formzuordnungen|Als Linie in das Modelldiagramm Domäne, verknüpfen eine Form mit der Domänenklasse, die angezeigt wird, oder einen Connector für die domänenbeziehung, die es anzeigt, wird ein flächenkartogramm angezeigt.|  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über domänenspezifische Sprachtools](../modeling/overview-of-domain-specific-language-tools.md)   
 [DSL-Tools – Glossar](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)   
 [Anpassen und Erweitern einer domänenspezifischen Sprache](../modeling/customizing-and-extending-a-domain-specific-language.md)



