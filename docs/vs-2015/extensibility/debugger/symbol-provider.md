---
title: Symbol-Anbieter | Microsoft-Dokumentation
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
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f09fbe350afff983bb5fefe880104201441430c3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47513543"
---
# <a name="symbol-provider"></a>Symbolanbieter
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Symbolanbieter](https://docs.microsoft.com/visualstudio/extensibility/debugger/symbol-provider).  
  
Eine Ausdrucksauswertungsfehler-Implementierung des Ausdrucks muss den symbolischen Debuginformationen vom Sprachcompiler generiert werden, um zu überprüfen, Variablen und Ausdrücke zugreifen. Dies erfolgt durch die Nutzung der Schnittstellen eines Symbol-Anbieters (SP), auch einen Symbol-Handler genannt.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] bietet SPs für verwalteten Code als auch systemeigenen Code, wobei das Dateiformat der Programmdatenbank (PDB)-Symbol. Es sei denn, es ist ein sicheres muss für Ihr Programm die Verwendung von Symbolen, die in einem benutzerdefinierten Format gespeichert, ist es empfohlen, die vom SPs [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="implementation-notes"></a>Hinweise zur Implementierung  
 Die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Debug-Engines für die Kommunikation mit der Common Language Runtime (CLR)-Schnittstellen mit SPs erwarten. Daher muss ein SP, die die Visual Studio-Debug-Engines verwendet werden, die CLR unterstützen. Eine vollständige Liste der alle CLR-Debugschnittstellen befinden sich debugref.doc, gehört der der [!INCLUDE[winsdklong](../../includes/winsdklong-md.md)].  
  
 Wenn Ihre SP nur mit Ihrer benutzerdefinierten Debug-Engine arbeiten, können Sie die SP implementieren, Bedarf je nach den Anforderungen der Debug-Engine.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggerkomponenten](../../extensibility/debugger/debugger-components.md)

