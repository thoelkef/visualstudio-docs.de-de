---
title: Symbol-Anbieter | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6af1af9d2e178241fa8a5957e18c1a5333fa4b09
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58961341"
---
# <a name="symbol-provider"></a>Symbolanbieter
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Eine Ausdrucksauswertungsfehler-Implementierung des Ausdrucks muss den symbolischen Debuginformationen vom Sprachcompiler generiert werden, um zu überprüfen, Variablen und Ausdrücke zugreifen. Dies erfolgt durch die Nutzung der Schnittstellen eines Symbol-Anbieters (SP), auch einen Symbol-Handler genannt.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] bietet SPs für verwalteten Code als auch systemeigenen Code, wobei das Dateiformat der Programmdatenbank (PDB)-Symbol. Es sei denn, es ist ein sicheres muss für Ihr Programm die Verwendung von Symbolen, die in einem benutzerdefinierten Format gespeichert, ist es empfohlen, die vom SPs [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="implementation-notes"></a>Hinweise zur Implementierung  
 Die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Debug-Engines für die Kommunikation mit der Common Language Runtime (CLR)-Schnittstellen mit SPs erwarten. Daher muss ein SP, die die Visual Studio-Debug-Engines verwendet werden, die CLR unterstützen. Eine vollständige Liste der alle CLR-Debugschnittstellen befinden sich debugref.doc, gehört der der [!INCLUDE[winsdklong](../../includes/winsdklong-md.md)].  
  
 Wenn Ihre SP nur mit Ihrer benutzerdefinierten Debug-Engine arbeiten, können Sie die SP implementieren, Bedarf je nach den Anforderungen der Debug-Engine.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggerkomponenten](../../extensibility/debugger/debugger-components.md)
