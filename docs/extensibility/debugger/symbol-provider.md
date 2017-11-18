---
title: Symbol-Anbieter | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f845e18bbd4c06d5652571ec83270a80d31ec852
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="symbol-provider"></a>Symbol-Anbieter
Eine Expression Evaluator-Implementierung muss die vom Sprachcompiler generiert werden, um zu überprüfen, Variablen und Ausdrücke symbolischen Debuginformationen zugreifen. Dies erfolgt durch die Nutzung von der Schnittstellen von einem Symbol-Anbieter (SP), auch einen Symbol-Handler aufgerufen.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]liefert SPs für verwalteten Code als auch systemeigenen Code mit dem Dateiformat der Programmdatenbank (PDB)-Symbol. Es sei denn, es ist ein sicheres müssen Sie für Ihr Programm die Verwendung von Symbolen, die in einem benutzerdefinierten Format gespeichert ist, wird empfohlen, die vom SPs verwenden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="implementation-notes"></a>Hinweise zur Implementierung  
 Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debugmodule sprechen Sie mit der Common Language Runtime (CLR)-Schnittstellen mit SPs erwarten. Daher muss ein SP, die mit Visual Studio-Debugmodule arbeiten, die CLR unterstützen. Eine vollständige Liste der alle CLR-Debugschnittstellen verwendbaren im debugref.doc, die Teil von der [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)].  
  
 Wenn die SP nur mit Ihrer benutzerdefinierten Debugmodul arbeiten, können Sie die SP implementieren, Sie je nach den Anforderungen Ihrer Debugging-Modul finden Sie unter passt.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggerkomponenten](../../extensibility/debugger/debugger-components.md)