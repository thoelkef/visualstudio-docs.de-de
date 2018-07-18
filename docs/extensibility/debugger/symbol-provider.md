---
title: Symbol-Anbieter | Microsoft Docs
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
ms.openlocfilehash: a98a5b80126bcb11109acedc2d24f226cde3714a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31126168"
---
# <a name="symbol-provider"></a>Symbol-Anbieter
Eine Expression Evaluator-Implementierung muss die vom Sprachcompiler generiert werden, um zu überprüfen, Variablen und Ausdrücke symbolischen Debuginformationen zugreifen. Dies erfolgt durch die Nutzung von der Schnittstellen von einem Symbol-Anbieter (SP), auch einen Symbol-Handler aufgerufen.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] liefert SPs für verwalteten Code als auch systemeigenen Code mit dem Dateiformat der Programmdatenbank (PDB)-Symbol. Es sei denn, es ist ein sicheres müssen Sie für Ihr Programm die Verwendung von Symbolen, die in einem benutzerdefinierten Format gespeichert ist, wird empfohlen, die vom SPs verwenden [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="implementation-notes"></a>Hinweise zur Implementierung  
 Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debugmodule sprechen Sie mit der Common Language Runtime (CLR)-Schnittstellen mit SPs erwarten. Daher muss ein SP, die mit Visual Studio-Debugmodule arbeiten, die CLR unterstützen. Eine vollständige Liste der alle CLR-Debugschnittstellen verwendbaren im debugref.doc, die Teil von der [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)].  
  
 Wenn die SP nur mit Ihrer benutzerdefinierten Debugmodul arbeiten, können Sie die SP implementieren, Sie je nach den Anforderungen Ihrer Debugging-Modul finden Sie unter passt.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggerkomponenten](../../extensibility/debugger/debugger-components.md)