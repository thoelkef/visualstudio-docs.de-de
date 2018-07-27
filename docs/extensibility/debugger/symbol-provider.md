---
title: Symbol-Anbieter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9d54494a8fa23e0714769863ac0fa2e5ddc1f4c2
ms.sourcegitcommit: 8d38d5d2f2b75fc1563952c0d6de0fe43af12766
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/26/2018
ms.locfileid: "39276974"
---
# <a name="symbol-provider"></a>Symbolanbieter
Eine Ausdrucksauswertungsfehler-Implementierung des Ausdrucks muss den symbolischen Debuginformationen vom Sprachcompiler generiert werden, um zu überprüfen, Variablen und Ausdrücke zugreifen. Dies erfolgt durch die Nutzung der Schnittstellen eines Symbol-Anbieters (SP), auch einen Symbol-Handler genannt.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bietet SPs für verwalteten Code als auch systemeigenen Code, wobei das Dateiformat der Programmdatenbank (PDB)-Symbol. Es sei denn, es ist ein sicheres muss für Ihr Programm die Verwendung von Symbolen, die in einem benutzerdefinierten Format gespeichert, ist es empfohlen, die vom SPs [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="implementation-notes"></a>Hinweise zur Implementierung  
 Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debug-Engines für die Kommunikation mit der Common Language Runtime (CLR)-Schnittstellen mit SPs erwarten. Daher muss ein SP, die die Visual Studio-Debug-Engines verwendet werden, die CLR unterstützen. Eine vollständige Liste der alle CLR-Debugschnittstellen befinden sich debugref.doc, gehört der der [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)].  
  
 Wenn Ihre SP nur mit Ihrer benutzerdefinierten Debug-Engine arbeiten, können Sie die SP implementieren, Bedarf je nach den Anforderungen der Debug-Engine.  
  
## <a name="see-also"></a>Siehe auch  
 [Debugger-Komponenten](../../extensibility/debugger/debugger-components.md)