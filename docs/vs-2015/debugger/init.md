---
title: Init | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c55ddec8-9101-4673-979b-4109caca9146
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d394ce2f149be842b42ffe4661cfbc361858bd71
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47514575"
---
# <a name="init"></a>Init
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Init](https://docs.microsoft.com/visualstudio/debugger/graphics/init).  
  
Bereitet die In-App-Komponente der Grafikdiagnose vor, um Grafikinformationen aktiv in einer Grafikprotokolldatei zu erfassen und aufzuzeichnen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
void Init(  
  std::function<void (int len, wchar_t * pszBuffer)> vsgLogGetter  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `vsgLogGetter`  
 Eine aufrufbare Entität, wie etwa eine Funktion, ein Funktionszeiger, Lambda oder ein Funktionsobjekt, die als Parameter die Länge eines Puffers verwendet, der aus `wchar_t` und einem Zeiger auf diesen Puffer besteht, und `void` zurückgibt. Wenn sie aufgerufen wird, bestimmt die aufrufbare Entität den Dateinamen, der verwendet wird, um Grafikinformationen aufzuzeichnen, und schreibt in den angegebenen Puffer, bevor eine Rückgabe erfolgt.  
  
## <a name="remarks"></a>Hinweise  
 Die `Init`-Funktion wird automatisch aufgerufen, wenn eine Instanz der `VsgDbg`-Klasse erstellt wird, indem der `bDefaultInit`-Parameter des Konstruktors auf `true` festgelegt wird. Andernfalls muss `Init` explizit aufgerufen werden, bevor Sie Grafikinformationen aktiv erfassen und aufzeichnen können.  
  
 Sie können die aktive Grafikprotokolldatei durch Aufrufen von `UnInit` abschließen und schließen und anschließend weitere Grafikinformationen in einer neuen Grafikprotokolldatei erfassen und aufzeichnen, indem Sie `Init` erneut aufrufen. Sie können dies so oft wiederholen, wie Sie möchten, um mehrere unabhängige Grafikprotokolldateien mithilfe derselben `VsgDbg`-Instanz zu erstellen.  
  
## <a name="see-also"></a>Siehe auch  
 [UnInit](../debugger/init.md)



