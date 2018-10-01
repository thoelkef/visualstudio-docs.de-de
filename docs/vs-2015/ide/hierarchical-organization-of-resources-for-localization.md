---
title: Hierarchische Organisation der Ressourcen für die Lokalisierung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- resource files, localized
- localization [Visual Studio], resources
- fallback resources
- international applications [Visual Studio], storing resources
- satellite assemblies, resource hierarchies
- globalization [Visual Studio], resources
- satellite assemblies
- resources [Visual Studio], fallback system
- resource files, fallback processes
ms.assetid: dadf8f2c-f74c-44d7-bec0-a1e956d8d38d
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0e07d788f17469ab7a478f22dcf3aeffacfa9220
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47522053"
---
# <a name="hierarchical-organization-of-resources-for-localization"></a>Hierarchische Organisation der Ressourcen für die Lokalisierung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio werden lokalisierte Ressourcen (kulturspezifische Daten wie Zeichenfolgen und Bilder) in separaten Dateien gespeichert und je nach Kultureinstellung der Benutzeroberfläche geladen. Um zu verstehen, wie lokalisierte Ressourcen geladen werden, ist es hilfreich, sie als auf hierarchische Weise organisiert zu betrachten.  
  
## <a name="kinds-of-resources-in-the-hierarchy"></a>Arten von Ressourcen in der Hierarchie  
  
-   Ganz oben in der Hierarchie befinden sich die Fallbackressourcen für Ihre Standardkultur, zum Beispiel Englisch („en“). Dies sind die einzigen Ressourcen, die keine eigene Datei haben; sie sind in der Hauptassembly gespeichert.  
  
-   Unterhalb der Fallbackressourcen befinden sich die Ressourcen für die neutralen Kulturen. Eine neutrale Kultur ist nicht einem Land/einer Region, sondern einer Sprache zugeordnet. Eine neutrale Kultur zum Beispiel Französisch („fr“). (Beachten Sie, dass die Fallbackressourcen zwar auch für eine neutrale Kultur gelten, aber für eine besondere.)  
  
-   Darunter befinden sich die Ressourcen für spezifische Kulturen. Eine spezifische Kultur ist einer Sprache und einem Land/einer Region zugeordnet. Eine spezifische Kultur ist zum Beispiel kanadisches Französisch („fr-CA“).  
  
 Wenn eine Anwendung versucht, eine lokalisierte Ressource, zum Beispiel eine Zeichenfolge, zu laden, diese aber nicht finden kann, wird die Hierarchie durchsucht, bis eine Ressourcendatei gefunden wird, die die angeforderte Ressource enthält.  
  
 Die beste Möglichkeit, Ihre Ressourcen zu speichern, ist sie so weit wie möglich zu generalisieren. Das bedeutet, dass lokalisierte Zeichenfolgen, Bilder usw. nach Möglichkeit in Ressourcendateien für neutrale und nicht für spezifische Kulturen gespeichert werden. Beispiel: Wenn Sie über Ressourcen für belgisches Französisch („fr-BE“) verfügen und die unmittelbar darüber liegenden Ressourcen die Fallbackressourcen in Englisch sind, könnte möglicherweise ein Problem entstehen, wenn jemand Ihre Anwendung auf einem für kanadisches Französisch konfigurierten System verwendet. Das System sucht nach einer Satellitenassembly für „fr-CA“, findet sie nicht und lädt dann nicht die französischen Ressourcen, sondern die Hauptassembly mit der englischen Fallbackressource. In der folgenden Abbildung wird dieses unerwünschte Szenario dargestellt.  
  
 ![Nur bestimmte Ressourcen](../ide/media/vbspecificresourcesonly.gif "vbSpecificResourcesOnly")  
  
 Wenn Sie der empfohlenen Vorgehensweise folgen und möglichst viele Ressourcen in einer neutralen Ressourcendatei für die Kultur „fr“ speichern, werden einem kanadisch-französischen Benutzer keine für die Kultur „fr-BE“ gekennzeichneten Ressourcen, sondern französische Zeichenfolgen angezeigt. In der folgenden Abbildung wird dieses bevorzugte Szenario dargestellt.  
  
 ![Grafik zu NeutralSpecificResources](../ide/media/vbneutralspecificresources.gif "vbNeutralSpecificResources")  
  
## <a name="see-also"></a>Siehe auch  
 [Neutrale Ressourcensprachen für die Lokalisierung](../ide/neutral-resources-languages-for-localization.md)   
 [Sicherheit und lokalisierte Satellitenassemblys](../ide/security-and-localized-satellite-assemblies.md)   
 [Lokalisieren von Anwendungen](../ide/localizing-applications.md)   
 [Globalisieren und Lokalisieren von Anwendungen](../ide/globalizing-and-localizing-applications.md)   
 [Gewusst wie: Festlegen der Kultur und Benutzeroberflächenkultur für die Windows Forms-Globalisierung](http://msdn.microsoft.com/en-us/694e049f-0b91-474a-9789-d35124f248f0)   
 [Gewusst wie: Festlegen der Kultur und Benutzeroberflächenkultur für die Globalisierung von ASP.NET-Webseiten](http://msdn.microsoft.com/library/76091f86-f967-4687-a40f-de87bd8cc9a0)

