---
title: Problembehandlung bei Codeausschnitten | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: troubleshooting
helpviewer_keywords:
- IntelliSense Code Snippets, troubleshooting
- troubleshooting IntelliSense Code Snippets
- troubleshooting Visual Basic, IntelliSense Code Snippets
ms.assetid: 7b6dd40e-2f78-4b50-8e68-41fac1bcb81e
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 61f1a623d5ee5edee376819ad6c385aead5003f8
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60117953"
---
# <a name="troubleshooting-snippets"></a>Problembehandlung bei Codeausschnitten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Probleme bei IntelliSense-Codeausschnitten sind häufig auf eine beschädigte Ausschnittsdatei oder auf fehlerhafte Inhalte in der Datei zurückzuführen.  
  
## <a name="common-problems"></a>Häufige Probleme  
  
### <a name="the-snippet-cannot-be-dragged-from-file-explorer-to-a-visual-studio-source-file"></a>Der Codeausschnitt lässt sich nicht vom Explorer in eine Visual Studio-Quelldatei ziehen  
  
- Der XML-Code in der Ausschnittsdatei ist möglicherweise fehlerhaft. Probleme mit der XML-Struktur können mithilfe des **XML-Editors** in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ermittelt werden.  
  
- Die Ausschnittsdatei entspricht nicht dem Ausschnittsschema. Probleme mit der XML-Struktur können mithilfe des **XML-Editors** in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ermittelt werden.  
  
### <a name="the-code-has-compiler-errors-that-are-not-highlighted"></a>Im Code befinden sich Compilerfehler, die nicht hervorgehoben werden  
  
- Möglicherweise ist ein Projektverweis nicht vorhanden. Lesen Sie die Dokumentation zu dem Codeausschnitt. Wenn der Verweis nicht auf dem Computer gefunden wird, müssen Sie diesen installieren. Durch das Einfügen eines Codeausschnitts sollten dem Projekt alle erforderlichen Verweise hinzugefügt werden. Wenn die Verweisinformationen nicht im Codeausschnitt vorhanden sind, kann dieser Fehler dem Ausschnittsersteller gemeldet werden.  
  
- Eine Variable wurde möglicherweise nicht definiert. Nicht definierte Variablen in einem Ausschnitt sollten hervorgehoben werden. Wenn dies nicht der Fall ist, kann dieser Fehler dem Ausschnittsersteller gemeldet werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Codeausschnitte](../ide/code-snippets.md)
