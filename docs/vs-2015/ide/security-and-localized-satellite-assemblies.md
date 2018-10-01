---
title: Sicherheit und lokalisierte Satellitenassemblys | Microsoft-Dokumentation
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
- key pairs for strong-named assemblies
- strong-named assemblies, security considerations
- satellite assemblies, localized
- code signing, assemblies
- security [Visual Studio], assemblies
- strong-named assemblies, localized
- assemblies [Visual Studio], security
- localization, satellite assemblies
ms.assetid: 6d953840-b301-47d5-8d34-30c1b29b5071
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8b530cb0f85eb112c98ff9d4de07f7256c5e69c9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47511423"
---
# <a name="security-and-localized-satellite-assemblies"></a>Sicherheit und lokalisierte Satellitenassemblys
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Ihre Hauptassembly einen starken Namen hat, müssen Satellitenassemblys mit dem gleichen privaten Schlüssel wie die Hauptassembly signiert werden. Wenn das öffentlich-private Schlüsselpaar der Haupt- und Satellitenassembly nicht das gleiche ist, können Ihre Ressourcen nicht geladen werden. Weitere Informationen zum Signieren von Assemblys finden Sie unter [Vorgehensweise: Signieren einer Assembly mit einem starken Namen](http://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67).  
  
 Generell müssen Sie möglicherweise die Signierungsgruppe Ihrer Organisation oder eine externe Signierungsorganisation mit dem privaten Schlüssel signieren lassen. Dies liegt daran, dass der private Schlüssel vertraulich ist: der Zugriff ist meist auf einige Wenige beschränkt. Während der Entwicklung können Sie das verzögerte Signieren einsetzen. Weitere Informationen finden Sie unter [Verzögertes Signieren einer Assembly](http://msdn.microsoft.com/library/9d300e17-5bf1-4360-97da-2aa55efd9070).  
  
## <a name="see-also"></a>Siehe auch  
 [Überlegungen zur Assemblysicherheit](http://msdn.microsoft.com/library/1b5439c1-f3d5-4529-bd69-01814703d067)   
 [Schlüsselbegriffe der Sicherheit](http://msdn.microsoft.com/library/3cfced4f-ea02-4e66-ae98-d69286363e98)   
 [Einführung in internationale Anwendungen basierend auf .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)   
 [Lokalisieren von Anwendungen](../ide/localizing-applications.md)   
 [Globalisieren und Lokalisieren von Anwendungen](../ide/globalizing-and-localizing-applications.md)

