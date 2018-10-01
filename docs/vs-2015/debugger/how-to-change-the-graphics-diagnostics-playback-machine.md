---
title: 'Vorgehensweise: Ändern Sie die Grafikdiagnose-Wiedergabecomputers | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1b9aa3ea-29a0-4e21-bc57-936f33537b5c
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e33d2acc46cbf92c9b2bbd699903ad3169661a54
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47514034"
---
# <a name="how-to-change-the-graphics-diagnostics-playback-machine"></a>Gewusst wie: Ändern des Grafikdiagnose-Wiedergabecomputers
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Vorgehensweise: Ändern Sie die Grafikdiagnose-Wiedergabecomputers](https://docs.microsoft.com/visualstudio/debugger/graphics/how-to-change-the-graphics-diagnostics-playback-machine).  
  
Sie können Grafikinformationen über Ihren lokalen Computer oder einen Remotecomputer bzw. ein Remotegerät wiedergeben.  
  
## <a name="choosing-a-playback-machine"></a>Auswählen eines Wiedergabecomputers  
 Der Wiedergabecomputer ist ein Computer oder ein Gerät zur Wiedergabe von Grafikereignissen aus einem Grafikprotokoll. Normalerweise ist der lokale Computer die zweckmäßigste Option, jedoch kann ein Renderingproblem möglicherweise nicht auf einem Computer reproduziert werden, der über unterschiedliche Hardware- oder Treiberversionen als der Computer verfügt, der zur Aufzeichnung verwendet wurde. Ist dies der Fall, können Sie einen Remotewiedergabecomputer auswählen, der das Problem besser reproduziert, und trotzdem Ihren Entwicklungscomputer zur Diagnose verwenden.  
  
#### <a name="to-use-the-local-machine-to-play-back-graphics-information"></a>So verwenden Sie den lokalen Computer, um Grafikinformationen wiederzugeben  
  
1.  Wählen Sie auf das Dokumentfenster "Grafikprotokolle", die **Wiedergabecomputer** Link. Die **Verbindungen des Remotedebuggers** Dialogfeld wird angezeigt.  
  
2.  Klicken Sie unter **manuelle Konfiguration**in die **Adresse** -Eigenschaft, geben Sie `localhost`.  
  
3.  Legen Sie die **Authentifizierungsmodus** Eigenschaft **keine**.  
  
4.  Wählen Sie die **wählen** Schaltfläche.  
  
#### <a name="to-use-a-remote-machine-to-play-back-graphics-information"></a>So verwenden Sie einen Remotecomputer zur Wiedergabe von Grafikinformationen  
  
1.  Wählen Sie auf das Dokumentfenster "Grafikprotokolle", die **Wiedergabecomputer** Link. Die **Verbindungen des Remotedebuggers** Dialogfeld wird angezeigt.  
  
2.  Klicken Sie unter **manuelle Konfiguration**in die **Adresse** -Eigenschaft, geben Sie die Windows-Domänennamen oder die IP-Adresse des Computers oder Geräts ein, die Sie zur Wiedergabe von Grafikinformationen verwenden möchten.  
  
3.  Geben Sie die Art der Autorisierung an, die Sie verwenden möchten, um die Verbindung mit dem Wiedergabecomputer zu sichern.  
  
    -   Legen Sie für die Windows-Authentifizierung die **Authentifizierungsmodus** Eigenschaft **Windows**.  
  
    -   Legen Sie für die keine Authentifizierung der **Authentifizierungsmodus** Eigenschaft **keine**.  
  
4.  Wählen Sie die **wählen** Schaltfläche.  
  
> [!NOTE]
>  Die **Verbindungen des Remotedebuggers** Dialogfeld kann auch remotedebuggingziele, die direkt auf Ihren Entwicklungscomputer verbunden sind oder sich im gleichen Subnetz anzeigen. Sie können eines dieser Remotedebuggingziele als Grafikdiagnose-Wiedergabecomputer verwenden, ohne diesen manuell zu konfigurieren. In der **Verbindungen des Remotedebuggers** Dialogfeld wählen das Ziel, Sie möchten, und wählen Sie dann, die **wählen** Schaltfläche.  
  
## <a name="see-also"></a>Siehe auch  
 [Grafikprotokolldokument](../debugger/graphics-log-document.md)



