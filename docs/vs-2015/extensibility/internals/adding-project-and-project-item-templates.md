---
title: Hinzufügen von Projekt und Projektelementvorlagen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], adding
- project items [Visual Studio], adding
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7ca77f2cfeb6dbab7a8d9be33bf7ba822f25d2a2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47508972"
---
# <a name="adding-project-and-project-item-templates"></a>Hinzufügen von Projekt- und Projektelementvorlagen
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Hinzufügen von Projekt- und Projektelementvorlagen](https://docs.microsoft.com/visualstudio/extensibility/internals/adding-project-and-project-item-templates).  
  
Wenn Sie eigene Projekttypen erstellen, müssen Sie die Unterstützung für neue Projekte und Projektelemente hinzufügen, mit der standardmäßigen bereitstellen [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Dialogfelder für Development Environment (IDE) integriert. Die folgenden Themen wird erläutert, verschiedene Verfahren zum Hinzufügen von Projekten und Projektelementen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Projektkontext](../../extensibility/internals/project-context.md)  
 Erklärt, dass das Projekt enthält den Großteil der Kontextinformationen für die in der Umgebung anrufsverkehrs.  
  
 [Projektpriorität](../../extensibility/internals/project-priority.md)  
 Erklärt, dass ein Projektelement in der Regel ein Member eines Projekts ist, um Mehrdeutigkeit zu vermeiden darüber, welche Projekt verwendet wird, um das Element zu öffnen.  
  
 [Verschiedene Projektdateien](../../extensibility/internals/miscellaneous-files-project.md)  
 Enthält Informationen zu den zwei Typen von Editoren, die zum Öffnen von Dateien in einem Projekt und die Rolle verwendet werden können, dass das Projekt spielt bei der Bestimmung der geeigneten Editors verwenden, wenn ein Projektelement geöffnet wird.  
  
 [Registrieren von Projekt- und Elementvorlagen](../../extensibility/internals/registering-project-and-item-templates.md)  
 Erläutert, was geschieht, wenn eine [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Projekt wird erstellt.  
  
 [Hinzufügen von Elementen zu den Dialogfeldern „Neues Element hinzufügen“](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)  
 Erläutert das Verfahren zum Hinzufügen von Elementen, die **neues Element hinzufügen** Dialogfeld.  
  
 [Hinzufügen von Verzeichnissen zum Dialogfeld „Neues Projekt“](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)  
 Enthält ein Beispiel der Registrierung eines neuen Verzeichnis, das benutzerdefinierte Vorlagen zur Verfügung gestellt, von einem VSPackage enthält.  
  
 [Hinzufügen von Verzeichnissen zum Dialogfeld „Neues Element hinzufügen“](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)  
 Enthält ein Beispiel für einen neuen Satz von Verzeichnissen, für die Registrierung der **neues Element hinzufügen** Dialogfeld.  
  
 [IDE-definierte Befehle zum Erweitern von Projektsystemen](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)  
 Listet verschiedene Typen der Befehl-Elemente, die zum Erweitern von Projektsystemen verwendet.  
  
 [CATIDs für Objekte, die in der Regel zum Erweitern von Projekten verwendet werden](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)  
 Listet CATIDs für Objekte, die verwendet werden, um erweitern [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)], [!INCLUDE[csprcs](../../includes/csprcs-md.md)], und [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] Projektsystemen.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Gewusst wie: Öffnen von projektspezifischen Editoren](../../extensibility/how-to-open-project-specific-editors.md)  
 Enthält schrittweise Anleitungen zum Öffnen eines Elements intrinsisch an einen bestimmten Editor für ein Projekt gebunden.  
  
 [Gewusst wie: Öffnen von Standard-Editoren](../../extensibility/how-to-open-standard-editors.md)  
 Enthält schrittweise Anleitungen für eine standard-Editor zu öffnen.  
  
 [Projektuntertypen](../../extensibility/internals/project-subtypes.md)  
 Enthält Links zu konzeptionellen Themen Untertyp Projekt. Projektuntertypen erweitert vorhandene [!INCLUDE[csprcs](../../includes/csprcs-md.md)] und [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] Projekte.  
  
 [Projekttypen](../../extensibility/internals/project-types.md)  
 Enthält Links zu weiteren Themen, die Informationen zum Entwerfen von neuen Projekttypen anbieten.

