---
title: "Erweitern Sie Abhängigkeitsdiagramme | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dependency diagrams, creating extensions
- layer models
ms.assetid: 83fca301-b008-485a-87eb-218050e71451
caps.latest.revision: 39
author: alexhomer1
ms.author: ahomer
manager: douge
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: ad673b1bc7d3089c37717dd7e1f1fce4e86d8100
ms.lasthandoff: 02/22/2017

---
# <a name="extend-dependency-diagrams"></a>Erweitern Sie Abhängigkeitsdiagramme
Sie können Code zum Erstellen und aktualisieren Abhängigkeitsdiagramme, und überprüfen Sie die Struktur des Programmcodes anhand von Abhängigkeitsdiagramme in Visual Studio schreiben. Sie können Befehle hinzufügen, die im Kontextmenü der Diagramme angezeigt werden, Drag & Drop-Gesten anpassen und über Textvorlagen auf das Ebenenmodell zugreifen. Sie können diese Erweiterung in einer Visual Studio Integration Extension (VSIX) verpacken und sie an andere Visual Studio-Benutzer verteilen.  
  
 Weitere Informationen zu Abhängigkeitsdiagramme finden Sie unter:  
  
-   [Abhängigkeitsdiagramme: Referenz](../modeling/layer-diagrams-reference.md)  
  
-   [Abhängigkeitsdiagramme: Richtlinien](../modeling/layer-diagrams-guidelines.md)  
  
-   [Erstellen Sie Abhängigkeitsdiagramme aus dem code](../modeling/create-layer-diagrams-from-your-code.md)  
  
-   [Überprüfen von Code mit Abhängigkeitsdiagramme](../modeling/validate-code-with-layer-diagrams.md)  
  
##  <a name="a-nameprereqsa-requirements"></a><a name="prereqs"></a> Anforderungen  
 Auf dem Computer, auf dem Sie die Ebenenerweiterungen entwickeln möchten, muss Folgendes installiert sein:  
  
-   Visual Studio  
  
-   [Visual Studio SDK](../extensibility/visual-studio-sdk.md)  
  
-   Modeling SDK für Visual Studio  


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

  
 Sie müssen die passende Visual Studio-Version auf dem Computer installiert haben, auf dem Sie die Ebenenerweiterungen ausführen möchten. Weitere Informationen finden Sie unter [bereitstellen eine Ebene Model-Erweiterung](../modeling/deploy-a-layer-model-extension.md).  
  
 Welche Versionen von Visual Studio Abhängigkeitsdiagramme unterstützen, finden Sie unter [versionsunterstützung für Architektur- und Modellierungstools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Hinzufügen von Befehlen und Gesten, Abhängigkeitsdiagramme](../modeling/add-commands-and-gestures-to-layer-diagrams.md)  
  
 [Hinzufügen von benutzerdefinierten architekturvalidierung Abhängigkeitsdiagramme](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)  
  
 [Fügen Sie benutzerdefinierter Eigenschaften zu Abhängigkeitsdiagramme hinzu](../modeling/add-custom-properties-to-layer-diagrams.md)  
  
 [Navigieren in und Aktualisieren von Ebenenmodellen im Programmcode](../modeling/navigate-and-update-layer-models-in-program-code.md)  
  
 [Bereitstellen einer Ebenenmodellerweiterung](../modeling/deploy-a-layer-model-extension.md)  
  
 [Problembehandlung bei Erweiterungen für Abhängigkeitsdiagramme](../modeling/troubleshoot-extensions-for-layer-diagrams.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Definieren und Installieren einer modellierungserweiterung](../modeling/define-and-install-a-modeling-extension.md)   
 [Abhängigkeitsdiagramme: Referenz](../modeling/layer-diagrams-reference.md)   
 [Abhängigkeitsdiagramme: Richtlinien](../modeling/layer-diagrams-guidelines.md)   
 [Erstellen Sie Abhängigkeitsdiagramme aus dem code](../modeling/create-layer-diagrams-from-your-code.md)   
 [Überprüfen von Code mit Abhängigkeitsdiagramme](../modeling/validate-code-with-layer-diagrams.md)   

