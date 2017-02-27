---
title: "How to: Include Prerequisites with a ClickOnce Application | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c66bf0a5-8c93-4e68-a224-3b29ac36fe4d
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# How to: Include Prerequisites with a ClickOnce Application
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Bevor Sie die erforderliche Software mit einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung verteilen können, müssen Sie zunächst die Installationspakete für diese erforderlichen Komponenten auf Ihren Entwicklungscomputer herunterladen.  Wenn Sie eine Anwendung veröffentlichen und **Erforderliche Komponenten von demselben Speicherort wie die Anwendung herunterladen** auswählen, tritt ein Fehler auf, wenn die Installationspakete nicht im Ordner **Pakete** enthalten sind.  
  
> [!NOTE]
>  Informationen zum Hinzufügen eines Installationspakets für .NET Framework finden Sie unter [Handbuch für die Bereitstellung von .NET Framework für Entwickler](http://msdn.microsoft.com/library/ee942965\(v=vs.110\).aspx).  
  
##  <a name="Package"></a> So fügen Sie mit Package.xml ein Installationspaket hinzu  
  
1.  Öffnen Sie im Datei\-Explorer den Ordner **Pakete**.  
  
     Der Pfad ist standardmäßig C:\\Programme\\Microsoft Visual Studio 14.0\\SDK\\Bootstrapper\\Packages auf einem 32\-Bit\-System und C:\\Programme \(x86\)\\Microsoft Visual Studio 14.0\\SDK\\Bootstrapper\\Packages auf einem 64\-Bit\-System.  
  
2.  Öffnen Sie den Ordner für die erforderliche Komponente, die Sie hinzufügen möchten, und öffnen Sie dann den Sprachordner für die installierte Version von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] \(z. B. **en** für Englisch\).  
  
3.  Öffnen Sie im Editor die Datei **Package.xml**.  
  
4.  Suchen Sie das **Name**\-Element, das **http:\/\/go.microsoft.com\/fwlink** enthält, und kopieren Sie die URL.  Schließen Sie die **LinkID**\-Komponente ein.  
  
    > [!NOTE]
    >  Wenn kein **Name**\-Element **http:\/\/go.microsoft.com\/fwlink** enthält, öffnen Sie die Datei **Product.xml** im Stammordner für die erforderliche Komponente, und suchen Sie die Zeichenfolge **fwlink**.  
  
    > [!IMPORTANT]
    >  Einige erforderliche Komponenten haben mehrere Installationspakete \(z. B. für 32\-Bit\- oder 64\-Bit\-Systeme\).  Wenn mehrere **Name**\-Elemente **fwlink** enthalten, müssen Sie die verbleibenden Schritte für jedes dieser Elemente überprüfen.  
  
5.  Fügen Sie die URL in die Adressleiste des Browsers ein, und wählen Sie dann, wenn Sie zum Ausführen oder Speichern aufgefordert werden, **Speichern** aus.  
  
     In diesem Schritt wird die Installationsdatei auf den Computer heruntergeladen.  
  
6.  Kopieren Sie die Datei in den Stammordner für die erforderliche Komponente.  
  
     Für die erforderliche Komponente von Windows Installer 4.5 kopieren Sie z. B. die Datei in den Ordner \\Packages\\WindowsInstaller4\_5.  
  
     Sie können das Installationspaket jetzt mit der Anwendung verteilen.  
  
## Siehe auch  
 [How to: Install Prerequisites with a ClickOnce Application](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)