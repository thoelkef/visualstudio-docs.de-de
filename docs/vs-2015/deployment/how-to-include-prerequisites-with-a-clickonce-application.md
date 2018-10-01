---
title: 'Vorgehensweise: Einschließen von erforderlichen Komponenten mit einer ClickOnce-Anwendung | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c66bf0a5-8c93-4e68-a224-3b29ac36fe4d
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: bd50b69bc46b1f00f797fd120351dd47f3bb8b03
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47509517"
---
# <a name="how-to-include-prerequisites-with-a-clickonce-application"></a>Gewusst wie: Einschließen von erforderlichen Komponenten mit einer ClickOnce-Anwendung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [wie: Einschließen von Voraussetzungen mit einer ClickOnce-Anwendung](https://docs.microsoft.com/visualstudio/deployment/how-to-include-prerequisites-with-a-clickonce-application).  
  
Bevor Sie die erforderliche Software mit einer [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]-Anwendung verteilen können, müssen Sie zunächst die Installationspakete für diese erforderlichen Komponenten auf Ihren Entwicklungscomputer herunterladen. Wenn Sie eine Anwendung veröffentlichen, und wählen Sie **erforderliche Komponenten von demselben Speicherort wie Anwendung herunterladen**, wird ein Fehler auftreten, wenn die Installationspakete nicht im der **Pakete** Ordner.  
  
> [!NOTE]
>  Zum Hinzufügen eines Installationspakets für .NET Framework finden Sie unter [Handbuch für die Bereitstellung von .NET Framework für Entwickler](http://msdn.microsoft.com/library/ee942965\(v=vs.110\).aspx).  
  
##  <a name="Package"></a> So fügen Sie ein Installationspaket, das mithilfe von "Package.xml" hinzu  
  
1.  Öffnen Sie im Datei-Explorer die **Pakete** Ordner.  
  
     Der Pfad ist standardmäßig C:\Programme\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages auf einem 32-Bit-System und C:\Programme (x86)\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages auf einem 64-Bit-System.  
  
2.  Öffnen Sie den Ordner für die erforderlichen Komponenten, die Sie hinzufügen möchten, und öffnen Sie dann den Sprachordner für die installierte Version von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (z. B. **En** für Englisch).  
  
3.  Öffnen Sie im Editor die **"Package.xml"** Datei.  
  
4.  Suchen Sie die **Namen** -Element mit **http://go.microsoft.com/fwlink**, und kopieren Sie die URL. Enthalten die **LinkID** Teil.  
  
    > [!NOTE]
    >  Wenn kein **Namen** Element enthält **http://go.microsoft.com/fwlink**öffnen die **Product.xml** Datei im Stammordner für die erforderliche Komponente, und suchen Sie die **Fwlink** Zeichenfolge.  
  
    > [!IMPORTANT]
    >  Einige erforderliche Komponenten haben mehrere Installationspakete (z. B. für 32-Bit- oder 64-Bit-Systeme). Wenn mehrere **Namen** Elemente enthalten **Fwlink**, Sie müssen die verbleibenden Schritte für jede von ihnen wiederholen.  
  
5.  Fügen Sie die URL in die Adressleiste Ihres Browsers, und wählen Sie Sie dann, wenn Sie Sie ausführen oder Speichern aufgefordert werden, **speichern**.  
  
     In diesem Schritt wird die Installationsdatei auf den Computer heruntergeladen.  
  
6.  Kopieren Sie die Datei in den Stammordner für die erforderliche Komponente.  
  
     Für die erforderliche Komponente von Windows Installer 4.5 kopieren Sie z. B. die Datei in den Ordner \Packages\WindowsInstaller4_5.  
  
     Sie können das Installationspaket jetzt mit der Anwendung verteilen.  
  
## <a name="see-also"></a>Siehe auch  
 [Gewusst wie: Installieren von erforderlichen Komponenten mit einer ClickOnce-Anwendung](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)



