---
title: Sprachdienst Unterstützung für das Debuggen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugger, language support
- language services, debugging support
ms.assetid: 7a44067f-a410-4a6a-84d2-bda5184140bc
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c61f7fa7e698e2c01cadb1dbb36a321c6e656e35
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195000"
---
# <a name="language-service-support-for-debugging"></a>Sprachdienstunterstützung für das Debuggen
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ein Sprachdienst kann Features bereitstellen, die einen Debugger über die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo> Schnittstelle unterstützen. Zu diesen Features gehören das Validieren von Haltepunkten und das Bereitstellen einer Liste von Ausdrücken **für das Fenster** "Auto".  
  
 Sie müssen jedoch über eine Ausdrucks Auswertung verfügen, um Ihre Sprache zu debuggen. Die Ausdrucks Auswertung ist für das Auswerten von Ausdrücken verantwortlich, damit beim Debuggen Werte erzeugt werden. Weitere Informationen zum Implementieren von CLR-Ausdrucks auswergratoren finden Sie unter:  
  
- [CLR-Ausdrucks Auswertung](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)  
  
- [Beispiel für Managed Expression Evaluator](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)  
  
## <a name="compiler-output"></a>Compilerausgabe  
 Der Compilertyp bestimmt, was Sie tun müssen, um das Debuggen für Ihre Sprache zu implementieren. Wenn der Compiler das Windows-Betriebssystem als Ziel hat und eine PDB-Datei schreibt, können Sie Programme mit der in Visual Studio integrierten Debug-Engine für System eigenes Code Debuggen. Wenn Ihr Compiler MSIL (Microsoft Intermediate Language) erstellt, können Sie Programme mit der Debug-Engine für verwaltetes Code Debuggen, die auch in Visual Studio integriert ist. Wenn der Compiler ein proprietäres Betriebssystem oder eine andere Laufzeitumgebung als Ziel hat, müssen Sie eine eigene Debug-Engine schreiben.  
  
 Weitere Informationen zum Implementieren des Debuggens für Ihre Sprache finden Sie unter [Getting Started](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) with the Visual Studio Debugging SDK.
