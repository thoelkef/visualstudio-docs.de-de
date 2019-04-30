---
title: 'Vorgehensweise: Einschließen von erforderlichen Komponenten mit einer ClickOnce-Anwendung | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
ms.assetid: c66bf0a5-8c93-4e68-a224-3b29ac36fe4d
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1c2f3bfe9fc40aa21e02268bb403d7497ac41529
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433827"
---
# <a name="how-to-include-prerequisites-with-a-clickonce-application"></a>Vorgehensweise: Einschließen von erforderlichen Komponenten mit einer ClickOnce-Anwendung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bevor Sie die erforderliche Software mit einer [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]-Anwendung verteilen können, müssen Sie zunächst die Installationspakete für diese erforderlichen Komponenten auf Ihren Entwicklungscomputer herunterladen. Wenn Sie eine Anwendung veröffentlichen, und wählen Sie **erforderliche Komponenten von demselben Speicherort wie Anwendung herunterladen**, wird ein Fehler auftreten, wenn die Installationspakete nicht im der **Pakete** Ordner.  
  
> [!NOTE]
> Zum Hinzufügen eines Installationspakets für .NET Framework finden Sie unter [Handbuch für die Bereitstellung von .NET Framework für Entwickler](http://msdn.microsoft.com/library/ee942965\(v=vs.110\).aspx).  
  
## <a name="Package"></a> So fügen Sie mit „Package.xml“ ein Installationspaket hinzu  
  
1. Öffnen Sie im Datei-Explorer den Ordner **Pakete**.  
  
     Der Pfad ist standardmäßig C:\Programme\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages auf einem 32-Bit-System und C:\Programme (x86)\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages auf einem 64-Bit-System.  
  
2. Öffnen Sie den Ordner für die erforderliche Komponente, die Sie hinzufügen möchten, und öffnen Sie dann den Sprachordner für die installierte Version von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (z.B. **en** für Englisch).  
  
3. Öffnen Sie im Editor die Datei **Package.xml**.  
  
4. Suchen Sie die **Namen** -Element mit **http://go.microsoft.com/fwlink**, und kopieren Sie die URL. Schließen Sie die **LinkID**-Komponente ein.  
  
    > [!NOTE]
    > Wenn kein **Namen** Element enthält **http://go.microsoft.com/fwlink**öffnen die **Product.xml** Datei im Stammordner für die erforderliche Komponente, und suchen Sie die **Fwlink** Zeichenfolge.  
  
    > [!IMPORTANT]
    > Einige erforderliche Komponenten haben mehrere Installationspakete (z. B. für 32-Bit- oder 64-Bit-Systeme). Wenn mehrere **Name**-Elemente **fwlink** enthalten, müssen Sie die verbleibenden Schritte für jedes dieser Elemente überprüfen.  
  
5. Fügen Sie die URL in die Adressleiste des Browsers ein, und wählen Sie dann, wenn Sie zum Ausführen oder Speichern aufgefordert werden, **Speichern** aus.  
  
     In diesem Schritt wird die Installationsdatei auf den Computer heruntergeladen.  
  
6. Kopieren Sie die Datei in den Stammordner für die erforderliche Komponente.  
  
     Für die erforderliche Komponente von Windows Installer 4.5 kopieren Sie z. B. die Datei in den Ordner \Packages\WindowsInstaller4_5.  
  
     Sie können das Installationspaket jetzt mit der Anwendung verteilen.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Installieren von erforderlichen Komponenten mit einer ClickOnce-Anwendung](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
