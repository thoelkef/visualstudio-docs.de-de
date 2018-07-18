---
title: 'Vorgehensweise: Einschließen von erforderlichen Komponenten mit einer ClickOnce-Anwendung | Microsoft Docs'
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
ms.openlocfilehash: 54cdcdb89896662a6d4e474c7df2ee09cea4d8bf
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
ms.locfileid: "31559058"
---
# <a name="how-to-include-prerequisites-with-a-clickonce-application"></a>Gewusst wie: Einschließen von erforderlichen Komponenten mit einer ClickOnce-Anwendung
Bevor Sie die erforderliche Software mit einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]-Anwendung verteilen können, müssen Sie zunächst die Installationspakete für diese erforderlichen Komponenten auf Ihren Entwicklungscomputer herunterladen. Wenn Sie eine Anwendung veröffentlichen, und wählen Sie **erforderliche Komponenten von demselben Speicherort wie Anwendung herunterladen**, wird eine Fehlermeldung angezeigt, wenn die Installationspakete nicht im die **Pakete** Ordner.  
  
> [!NOTE]
>  Um ein Installationspaket für .NET Framework hinzuzufügen, finden Sie unter [Handbuch für die Bereitstellung von .NET Framework für Entwickler](http://msdn.microsoft.com/library/ee942965\(v=vs.110\).aspx).  
  
##  <a name="Package"></a> So fügen Sie ein Installationspaket, das mithilfe von "Package.xml" hinzu  
  
1.  Öffnen Sie im Datei-Explorer die **Pakete** Ordner.  
  
     Der Pfad ist standardmäßig C:\Programme\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages auf einem 32-Bit-System und C:\Programme (x86)\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages auf einem 64-Bit-System.  
  
2.  Öffnen Sie den Ordner für die erforderlichen Komponenten, die Sie hinzufügen möchten, und öffnen Sie dann den Sprachordner für die installierte Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] (z. B. **En** für Englisch).  
  
3.  Öffnen Sie im Editor die **"Package.xml"** Datei.  
  
4.  Suchen Sie die **Namen** Element, das enthält **http://go.microsoft.com/fwlink**, und kopieren Sie die URL. Enthalten die **LinkID** Teil.  
  
    > [!NOTE]
    >  Wenn kein **Namen** Element enthält **http://go.microsoft.com/fwlink**öffnen die **Product.xml** Datei im Stammordner für die erforderliche Komponente, und suchen Sie die **Fwlink** Zeichenfolge.  
  
    > [!IMPORTANT]
    >  Einige erforderliche Komponenten haben mehrere Installationspakete (z. B. für 32-Bit- oder 64-Bit-Systeme). Wenn mehrere **Namen** Elemente enthalten **Fwlink**, müssen Sie die verbleibenden Schritte für jede von ihnen wiederholen.  
  
5.  Fügen Sie die URL in die Adressleiste des Browsers ein, und klicken Sie dann, wenn Sie aufgefordert werden, auszuführen oder zu speichern, wählen Sie **speichern**.  
  
     In diesem Schritt wird die Installationsdatei auf den Computer heruntergeladen.  
  
6.  Kopieren Sie die Datei in den Stammordner für die erforderliche Komponente.  
  
     Für die erforderliche Komponente von Windows Installer 4.5 kopieren Sie z. B. die Datei in den Ordner \Packages\WindowsInstaller4_5.  
  
     Sie können das Installationspaket jetzt mit der Anwendung verteilen.  
  
## <a name="see-also"></a>Siehe auch  
 [Gewusst wie: Installieren von erforderlichen Komponenten mit einer ClickOnce-Anwendung](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)