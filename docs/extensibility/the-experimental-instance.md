---
title: "Die experimentelle Instanz | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "experimentelle builds"
  - "VSPackages experimentelle builds"
  - "VSIP experimentelle builds"
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
caps.latest.revision: 36
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 36
---
# Die experimentelle Instanz
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Zum Schutz der Visual Studio\-Entwicklungsumgebung nicht getestete Anwendung, die sie ändern können, dient die VSSDK eines experimentelle, mit denen Sie experimentieren können. Sie entwickeln neue Anwendungen mithilfe von Visual Studio wie gewohnt, aber Sie ausführen, indem Sie mithilfe einer experimentellen Instanz.  
  
 Jede Anwendung, die ein VSIX\-Paket wird die experimentelle Visual Studio\-Instanz im Debugmodus gestartet.  
  
 Wenn Sie die experimentelle Instanz von Visual Studio außerhalb einer bestimmten Projektmappe starten möchten, führen Sie den folgenden Befehl in das Befehlsfenster ein:  
  
 "*\< visual Studio\-Installationspfad \>*\\Common7\\IDE\\devenv.exe" RootSuffix Exp  
  
> [!NOTE]
>  Die experimentelle Instanz bezieht sich auf die Registrierung unter dem `<version number>Exp` und `<version number>Exp_Config` Knoten. Zum Beispiel ist Visual Studio 2015 experimentelle Registrierungsbereich  
>   
>  `HKCU\Software\Microsoft\VisualStudio\14.0Exp` und `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`  
  
 Es wird empfohlen, dass Sie die Erweiterung in der experimentellen Instanz ausführen, während Sie es entwickeln. Wenn Sie die Erweiterung bereitstellen, wird die Entwicklungsinstanz. Weitere Informationen zum Registrieren von Anwendungen finden Sie unter [Registrieren von VSPackages](../extensibility/internals/registering-vspackages.md).