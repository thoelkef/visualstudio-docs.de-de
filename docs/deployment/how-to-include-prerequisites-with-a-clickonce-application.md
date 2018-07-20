---
title: 'Vorgehensweise: Einschließen von erforderlichen Komponenten mit einer ClickOnce-Anwendung | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
ms.assetid: c66bf0a5-8c93-4e68-a224-3b29ac36fe4d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3f961229e60cb291efdd7630f9df10e162c2f17b
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2018
ms.locfileid: "39153841"
---
# <a name="how-to-include-prerequisites-with-a-clickonce-application"></a>Gewusst wie: Einschließen von erforderlichen Komponenten mit einer ClickOnce-Anwendung
Bevor Sie die erforderliche Software mit einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]-Anwendung verteilen können, müssen Sie zunächst die Installationspakete für diese erforderlichen Komponenten auf Ihren Entwicklungscomputer herunterladen. Wenn Sie eine Anwendung veröffentlichen, und wählen Sie **erforderliche Komponenten von demselben Speicherort wie Anwendung herunterladen**, wird ein Fehler auftreten, wenn die Installationspakete nicht im der **Pakete** Ordner.  
  
> [!NOTE]
>  Zum Hinzufügen eines Installationspakets für .NET Framework finden Sie unter [Handbuch für die Bereitstellung von .NET Framework für Entwickler](http://msdn.microsoft.com/library/ee942965\(v=vs.110\).aspx).  
  
##  <a name="Package"></a> So fügen Sie ein Installationspaket, das mithilfe von "Package.xml" hinzu  
  
1.  Öffnen Sie im Datei-Explorer die **Pakete** Ordner.  
  
     Standardmäßig ist der Pfad *C:\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages* auf einem 32-Bit-System und *C:\Program Files (x86) \Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages* auf einem 64-Bit-System.  
  
2.  Öffnen Sie den Ordner für die erforderlichen Komponenten, die Sie hinzufügen möchten, und öffnen Sie dann den Sprachordner für die installierte Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] (z. B. **En** für Englisch).  
  
3.  Öffnen Sie im Editor die *"Package.xml"* Datei.  
  
4.  Suchen Sie die **Namen** -Element mit **http://go.microsoft.com/fwlink**, und kopieren Sie die URL. Enthalten die **LinkID** Teil.  
  
    > [!NOTE]
    >  Wenn kein **Namen** Element enthält **http://go.microsoft.com/fwlink**öffnen die **Product.xml** Datei im Stammordner für die erforderliche Komponente, und suchen Sie die **Fwlink** Zeichenfolge.  
  
    > [!IMPORTANT]
    >  Einige erforderliche Komponenten haben mehrere Installationspakete (z. B. für 32-Bit- oder 64-Bit-Systeme). Wenn mehrere **Namen** Elemente enthalten **Fwlink**, Sie müssen die verbleibenden Schritte für jede von ihnen wiederholen.  
  
5.  Fügen Sie die URL in die Adressleiste Ihres Browsers, und wählen Sie Sie dann, wenn Sie Sie ausführen oder Speichern aufgefordert werden, **speichern**.  
  
     In diesem Schritt wird die Installationsdatei auf den Computer heruntergeladen.  
  
6.  Kopieren Sie die Datei in den Stammordner für die erforderliche Komponente.  
  
     Kopieren Sie beispielsweise die Datei für die Windows Installer 4.5 erforderliche Komponente, die *\Packages\WindowsInstaller4_5* Ordner.  
  
     Sie können das Installationspaket jetzt mit der Anwendung verteilen.  
  
## <a name="see-also"></a>Siehe auch  
 [Gewusst wie: Installieren von Voraussetzungen mit einer ClickOnce-Anwendung](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)