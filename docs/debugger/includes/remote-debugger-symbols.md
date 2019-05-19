---
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.openlocfilehash: 26d9169be242990b9ca99b4fe4fe043d56fb7f30
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65839642"
---
Sie sollten Ihren Code mit den auf dem Visual Studio-Computer generierten Symbolen debuggen können. Die Leistung des Remotedebuggers ist viel besser, wenn Sie lokale Symbole verwenden.  Wenn Sie Remotesymbole verwenden müssen, ist es erforderlich, dem Remotedebugmonitor mitzuteilen, dass er auf dem Remotecomputer nach Symbolen suchen soll.  

Ab Visual Studio 2013 Update 2 können Sie über die folgende msvsmon-Befehlszeilenoption Remotesymbole für verwalteten Code verwenden: `Msvsmon /FallbackLoadRemoteManagedPdbs`  

Weitere Informationen finden Sie in der Hilfe zum Remotedebugging (drücken Sie **F1** im Remotedebuggerfenster, oder klicken Sie auf **Hilfe > Verwendung**). Weitere Informationen finden Sie unter [.NET Remote Symbol Loading Changes in Visual Studio 2012 and 2013 (Änderungen beim Laden von Symbolen in der .NET-Remoteinstanz in Visual Studio 2012 und 2013)](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013.aspx).
