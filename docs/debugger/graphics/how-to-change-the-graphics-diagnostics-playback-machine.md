---
title: 'Vorgehensweise: Ändern des Grafikdiagnose-Wiedergabecomputers | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
ms.assetid: 1b9aa3ea-29a0-4e21-bc57-936f33537b5c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 261714c530c2db36b64d7ef07aa19369b3f459bf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-change-the-graphics-diagnostics-playback-machine"></a>Gewusst wie: Ändern des Grafikdiagnose-Wiedergabecomputers
Sie können Grafikinformationen über Ihren lokalen Computer oder einen Remotecomputer bzw. ein Remotegerät wiedergeben.  
  
## <a name="choosing-a-playback-machine"></a>Auswählen eines Wiedergabecomputers  
 Der Wiedergabecomputer ist ein Computer oder ein Gerät zur Wiedergabe von Grafikereignissen aus einem Grafikprotokoll. Normalerweise ist der lokale Computer die zweckmäßigste Option, jedoch kann ein Renderingproblem möglicherweise nicht auf einem Computer reproduziert werden, der über unterschiedliche Hardware- oder Treiberversionen als der Computer verfügt, der zur Aufzeichnung verwendet wurde. Ist dies der Fall, können Sie einen Remotewiedergabecomputer auswählen, der das Problem besser reproduziert, und trotzdem Ihren Entwicklungscomputer zur Diagnose verwenden.  
  
#### <a name="to-use-the-local-machine-to-play-back-graphics-information"></a>So verwenden Sie den lokalen Computer, um Grafikinformationen wiederzugeben  
  
1.  Wählen Sie auf die Grafikprotokoll-Dokumentfenster angezeigt, die **Wiedergabecomputer** Link. Die **Verbindungen des Remotedebuggers** Dialogfeld wird angezeigt.  
  
2.  Klicken Sie unter **manuelle Konfiguration**in der **Adresse** -Eigenschaft, geben Sie `localhost`.  
  
3.  Legen Sie die **Authentifizierungsmodus** Eigenschaft **keine**.  
  
4.  Wählen Sie die **wählen** Schaltfläche.  
  
#### <a name="to-use-a-remote-machine-to-play-back-graphics-information"></a>So verwenden Sie einen Remotecomputer zur Wiedergabe von Grafikinformationen  
  
1.  Wählen Sie auf die Grafikprotokoll-Dokumentfenster angezeigt, die **Wiedergabecomputer** Link. Die **Verbindungen des Remotedebuggers** Dialogfeld wird angezeigt.  
  
2.  Klicken Sie unter **manuelle Konfiguration**in der **Adresse** -Eigenschaft, geben Sie den Windows-Domänennamen oder die IP-Adresse des Computers oder Geräts, das Sie zum Wiedergeben von Grafikinformationen verwenden möchten.  
  
3.  Geben Sie die Art der Autorisierung an, die Sie verwenden möchten, um die Verbindung mit dem Wiedergabecomputer zu sichern.  
  
    -   Legen Sie für Windows-Authentifizierung die **Authentifizierungsmodus** Eigenschaft **Windows**.  
  
    -   Legen Sie für die keine Authentifizierung der **Authentifizierungsmodus** Eigenschaft **keine**.  
  
4.  Wählen Sie die **wählen** Schaltfläche.  
  
> [!NOTE]
>  Die **Verbindungen des Remotedebuggers** Dialogfeld möglicherweise auch remotedebuggingziele, die direkt mit dem Entwicklungscomputer verbunden sind oder im gleichen Subnetz werden angezeigt. Sie können eines dieser Remotedebuggingziele als Grafikdiagnose-Wiedergabecomputer verwenden, ohne diesen manuell zu konfigurieren. In der **Verbindungen des Remotedebuggers** Dialogfeld wählen das Ziel, Sie möchten, und wählen Sie dann, die **wählen** Schaltfläche.  
  
## <a name="see-also"></a>Siehe auch  
 [Grafikprotokolldokument](graphics-log-document.md)