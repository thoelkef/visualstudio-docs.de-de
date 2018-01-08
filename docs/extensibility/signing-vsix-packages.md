---
title: Signieren die VSIX-Pakete | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ec875e6877b1c3ff1edf38b29c5e72b757021085
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2018
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