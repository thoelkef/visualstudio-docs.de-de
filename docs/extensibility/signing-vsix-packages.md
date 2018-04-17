---
title: Signieren die VSIX-Pakete | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 84166ed96fb49567f4ede3e8e0c4b7e8ba3cc814
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="signing-vsix-packages"></a>Signieren Sie die VSIX-Pakete
Erweiterungsassemblys müssen nicht signiert werden, bevor sie in Visual Studio ausgeführt werden können, aber es empfiehlt sich zu diesem Zweck ist.  
  
 Wenn Sie möchten Ihre Erweiterung sichern und stellen Sie sicher, dass er nicht manipuliert wurde, können Sie eine digitale Signatur zu einem VSIX-Paket hinzufügen. Wenn Sie eine VSIX signiert ist, wird das VSIX-Installationsprogramm eine Meldung, dass es, sowie weitere Informationen zur Signatur selbst signiert ist angezeigt. Wenn der Inhalt des VSIX-Pakete geändert wurden und VSIX-Pakete nicht erneut signiert wurde, wird das VSIX-Installationsprogramm angezeigt, dass die Signatur nicht gültig ist. Die Installation wurde nicht beendet, aber der Benutzer wird gewarnt.  
  
> [!IMPORTANT]
>  2015 ab, werden VSIX-Pakete, die mit etwas anderes als Verschlüsselung SHA256 signiert identifiziert werden, als hätte eine ungültige Signatur. VSIX-Installation wird nicht blockiert, jedoch wird der Benutzer darüber informiert werden.  
  
## <a name="signing-a-vsix-with-vsixsigntool"></a>Signieren Sie eine VSIX mit VSIXSignTool  
 Es ist eine Verschlüsselung mit einem SHA256 Signieren Tool verfügbar [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility) auf nuget.org am [VsixSignTool](http://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool).  
  
#### <a name="to-use-the-vsixsigntool"></a>Verwenden Sie die VSIXSignTool  
  
1.  Fügen Sie die VSIX zu einem Projekt hinzu.  
  
2.  Klicken Sie mit der rechten Maustaste auf den Projektknoten im Projektmappen-Explorer auswählen **hinzufügen &#124; NuGet-Pakete verwalten**.  Weitere Informationen zu NuGet und Hinzufügen von NuGet-Paketen finden Sie unter finden Sie unter der [NuGet-Dokumentation](/NuGet) und [Paket-Manager-UI](/NuGet/Tools/Package-Manager-UI) Themen.  
  
3.  VSIXSignTool aus VisualStudioExtensibility suchen Sie, und installieren Sie das NuGet-Paket.  
  
4.  Sie können jetzt die VSIXSignTool aus den Projektspeicherort Lokale Pakete ausführen. Wenden Sie sich an das Tool Befehlszeilenhilfe für Ihr Szenario signieren (VSIXSignTool.exe /?).  
  
 Z. B. zum Anmelden mit einem Kennwort geschützt Zertifikatdatei:  
  
 VSIXSignTool.exe Anmeldung/f \<Zertifikatdatei >/p \<Kennwort > \<VSIXfile >  
  
## <a name="see-also"></a>Siehe auch  
 [Bereitstellen von Visual Studio-Erweiterungen](../extensibility/shipping-visual-studio-extensions.md)