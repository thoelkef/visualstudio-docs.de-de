---
title: Symbolanbieter | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 31b90846d9494ee046cf9dc4a3e5de9ff033ea3f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712820"
---
# <a name="symbol-provider"></a>Symbolanbieter
Eine Expressionevaluatorimplementierung muss auf die symbolischen Debuginformationen zugreifen, die vom Sprachcompiler generiert werden, um Variablen und Ausdrücke auszuwerten. Dies geschieht, indem die Schnittstellen eines Symbolanbieters (SP) verwendet werden, der auch als Symbolhandler bezeichnet wird.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]liefert SPs für verwalteten Code sowie systemeigenen Code mithilfe des Programmdatendatenbank-Symboldateiformats (PDB). Es sei denn, Es besteht ein starker Bedarf für Ihr Programm, Symbole zu verwenden, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]die in einem benutzerdefinierten Format gespeichert sind, es wird empfohlen, die von bereitgestellten SPs zu verwenden.

## <a name="implementation-notes"></a>Hinweise zur Implementierung
 Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debug-Engines erwarten, mit den SPs über CLR-Schnittstellen (Common Language Runtime) zu sprechen. Daher muss ein SP, der mit den Visual Studio-Debugmodulen arbeitet, die CLR unterstützen. Eine vollständige Liste aller CLR-Debugging-Schnittstellen finden Sie in debugref.doc, das Teil der [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)]ist.

 Wenn Ihr SP nur mit Ihrem benutzerdefinierten Debugmodul funktioniert, können Sie den SP je nach den Anforderungen des Debugmoduls so implementieren, wie Sie es für richtig halten.

## <a name="see-also"></a>Weitere Informationen
- [Debugger-Komponenten](../../extensibility/debugger/debugger-components.md)
