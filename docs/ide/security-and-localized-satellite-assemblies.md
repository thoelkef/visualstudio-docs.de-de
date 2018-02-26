---
title: Sicherheit und lokalisierte Satellitenassemblys | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 5f2834e267e2494f62f5cfed9121a0a94a22afb0
ms.sourcegitcommit: a07b789cc41ed72664f2c700c1f114476e7b0ddd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2018
---
# <a name="security-and-localized-satellite-assemblies"></a>Sicherheit und lokalisierte Satellitenassemblys

Wenn Ihre Hauptassembly einen starken Namen hat, müssen Satellitenassemblys mit dem gleichen privaten Schlüssel wie die Hauptassembly signiert werden. Wenn das öffentlich-private Schlüsselpaar der Haupt- und Satellitenassembly nicht das gleiche ist, können Ihre Ressourcen nicht geladen werden. Weitere Informationen zum Signieren von Assemblys finden Sie unter [Vorgehensweise: Signieren einer Assembly mit einem starken Namen](/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name).  
  
 Generell müssen Sie möglicherweise die Signierungsgruppe Ihrer Organisation oder eine externe Signierungsorganisation mit dem privaten Schlüssel signieren lassen. Dies liegt daran, dass der private Schlüssel vertraulich ist: der Zugriff ist meist auf einige Wenige beschränkt. Während der Entwicklung können Sie das verzögerte Signieren einsetzen. Weitere Informationen finden Sie unter [Verzögertes Signieren einer Assembly](/dotnet/framework/app-domains/delay-sign-assembly).  
  
## <a name="see-also"></a>Siehe auch

- [Überlegungen zur Assemblysicherheit](/dotnet/framework/app-domains/assembly-security-considerations)  - [Schlüsselbegriffe der Sicherheit](/dotnet/standard/security/key-security-concepts)   
- [Einführung in internationale Anwendungen basierend auf .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)   
- [Lokalisieren von Anwendungen](../ide/localizing-applications.md)   
- [Globalisieren und Lokalisieren von Anwendungen](../ide/globalizing-and-localizing-applications.md)