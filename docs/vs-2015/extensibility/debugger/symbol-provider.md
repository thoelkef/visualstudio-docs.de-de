---
title: Symbol Anbieter | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68178892"
---
# <a name="symbol-provider"></a>Symbolanbieter
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Eine Ausdrucks Auswertungs Implementierung muss auf die symbolischen Debuginformationen zugreifen, die vom sprach Compiler generiert werden, um Variablen und Ausdrücke auszuwerten. Dies erfolgt durch die Verwendung der Schnittstellen eines Symbol Anbieters (SP), auch als Symbol Handler bezeichnet.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] bietet SPS für verwalteten Code sowie systemeigenen Code unter Verwendung des Symbol Datei Formats der Programmdatenbank (PDB). Es wird empfohlen, dass Sie die von bereitgestellten SPS verwenden, es sei denn, es besteht die Notwendigkeit, dass Ihr Programm in einem benutzerdefinierten Format gespeicherte Symbole verwendet [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="implementation-notes"></a>Hinweise zur Implementierung  
 Die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Debug-engines erwarten mit dem SPS mithilfe von CLR-Schnittstellen (Common Language Runtime). Folglich muss ein SP, der mit den Visual Studio-debuggingmodulen arbeiten wird, die CLR unterstützen. Eine vollständige Liste aller CLR-Debugschnittstellen finden Sie in debugref.doc, die Teil von ist [!INCLUDE[winsdklong](../../includes/winsdklong-md.md)] .  
  
 Wenn Ihr SP nur mit der benutzerdefinierten Debug-Engine funktioniert, können Sie den SP abhängig von den Anforderungen Ihrer Debug-Engine entsprechend implementieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Debuggerkomponenten](../../extensibility/debugger/debugger-components.md)
