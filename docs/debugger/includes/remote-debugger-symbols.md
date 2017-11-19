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
ms.openlocfilehash: 95d76781f651b681b81e4dd18848b404d8a85664
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
 Sie sollten Ihren Code mit den auf dem Visual Studio-Computer generierten Symbolen debuggen können. Die Leistung des Remotedebuggers ist viel besser, wenn Sie lokale Symbole verwenden.  Wenn Sie Remotesymbole verwenden müssen, ist es erforderlich, dem Remotedebugmonitor mitzuteilen, dass er auf dem Remotecomputer nach Symbolen suchen soll.  
  
 Ab Visual Studio 2013 Update 2 können können Sie die folgende Msvsmon-Befehlszeilenoption remotesymbole für verwalteten Code verwenden:`Msvsmon /FallbackLoadRemoteManagedPdbs`  
  
 Weitere Informationen finden Sie in der Hilfe zum Remotedebugging (drücken Sie **F1** im Remotedebugger-Fenster, oder klicken Sie auf **Hilfe > Verwendung**). Weitere Informationen zur finden Sie [.NET Remote Symbol Loading Changes in Visual Studio 2012 und 2013](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013.aspx)