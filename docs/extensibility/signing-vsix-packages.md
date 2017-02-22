---
title: "Signieren von VSIX-Paketen | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Signatur"
  - "Signieren"
  - "Authenticode"
  - "VSIX"
  - "Pakete"
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Signieren von VSIX-Paketen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Assemblys müssen nicht signiert werden, bevor sie in Visual Studio ausführen können, aber es empfiehlt sich, dafür ist.  
  
 Wenn Sie möchten Ihre Erweiterung sichern und stellen Sie sicher, dass sie nicht manipuliert wurde, können Sie einem VSIX\-Paket eine digitale Signatur hinzufügen. Wenn eine VSIX signiert ist, wird das VSIX\-Installationsprogramm eine Meldung, dass es, sowie weitere Informationen über die Signatur selbst signiert ist angezeigt. Wenn der Inhalt des VSIX\-Projekt geändert wurden und der VSIX\-Datei nicht erneut signiert wurde, wird das VSIX\-Installationsprogramm anzeigen, dass die Signatur nicht gültig ist. Die Installation wird nicht beendet, aber der Benutzer wird gewarnt.  
  
> [!IMPORTANT]
>  Ab 2015 werden VSIX\-Pakete mit etwas anderes als Verschlüsselung SHA256 signiert identifiziert werden, als hätten Sie eine ungültige Signatur. VSIX\-Installation wird nicht blockiert, aber der Benutzer darauf hingewiesen.  
  
## Signieren einer VSIX\-Datei mit VSIXSignTool  
 Es ist ein SHA256 Signieren von verfügbaren Tools [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility) unter "NuGet.org" unter [VsixSignTool](http://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool).  
  
#### Verwenden Sie die VSIXSignTool  
  
1.  Ihre VSIX zu einem Projekt hinzufügen.  
  
2.  Klicken Sie mit der rechten Maustaste auf den Projektknoten im Projektmappen\-Explorer auswählen **Hinzufügen &#124; NuGet\-Pakete verwalten**.  Weitere Informationen über NuGet und Hinzufügen von NuGet\-Pakete, finden Sie unter [NuGet\-Übersicht](http://docs.nuget.org/) und [Verwalten von NuGet\-Paketen mithilfe des Dialogs](http://docs.nuget.org/Consume/Package-Manager-Dialog).  
  
3.  VSIXSignTool aus VisualStudioExtensibility suchen Sie, und installieren Sie das NuGet\-Paket.  
  
4.  Sie können jetzt die VSIXSignTool aus den Projektspeicherort Lokale Pakete ausführen. Wenden Sie sich an die Hilfe des Tools über die Befehlszeile für das Signaturzertifikat Szenario \(VSIXSignTool.exe \/?\).  
  
 Zum Beispiel können Sie mit einem Kennwort geschützten Zertifikat\-Datei zu signieren:  
  
 VSIXSignTool.exe Anmeldung\/f \< Zertifikatdatei \>\/p \< Kennwort \>\< VSIXfile \>  
  
## Siehe auch  
 [Lieferung von Visual Studio\-Erweiterungen](../extensibility/shipping-visual-studio-extensions.md)