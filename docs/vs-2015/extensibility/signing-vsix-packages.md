---
title: Signieren von VSIX-Paketen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 56ddcae38593d35bc8a31628bf3087dc79ca25c4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51732545"
---
# <a name="signing-vsix-packages"></a>Signieren von VSIX-Paketen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Assemblys müssen nicht signiert werden, bevor sie in Visual Studio ausführen können, aber es empfiehlt sich, dafür ist.  
  
 Wenn Sie möchten Ihre Erweiterung zur sicheren, und stellen Sie sicher, dass sie nicht manipuliert wurde, können Sie eine digitale Signatur zu VSIX Package hinzufügen. Bei einer VSIX-Datei signiert ist, wird das VSIX-Installationsprogramm eine Meldung gibt an, dass es, sowie weitere Informationen über die Signatur selbst signiert ist angezeigt. Wenn der Inhalt des VSIX-Projekt geändert wurden, und die VSIX-Datei nicht erneut signiert wurde, zeigt das VSIX-Installationsprogramm, dass die Signatur nicht gültig ist. Die Installation nicht beendet wird, aber der Benutzer wird gewarnt.  
  
> [!IMPORTANT]
>  Von 2015 werden VSIX-Pakete, die mit etwas anderes als die Verschlüsselung mit SHA256 signiert identifiziert werden, wie eine ungültige Signatur. VSIX-Installation wird nicht blockiert, aber der Benutzer wird gewarnt werden.  
  
## <a name="signing-a-vsix-with-vsixsigntool"></a>Signieren einer VSIX-Datei mit VSIXSignTool  
 Es gibt eine SHA256-Verschlüsselung, Signierung von verfügbaren Tools [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility) auf nuget.org auf [VsixSignTool](http://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool).  
  
#### <a name="to-use-the-vsixsigntool"></a>Verwenden Sie die VSIXSignTool  
  
1. VSIX zu einem Projekt hinzufügen.  
  
2. Klicken Sie mit der rechten Maustaste auf den Projektknoten im Projektmappen-Explorer auswählen **hinzufügen &#124; NuGet-Pakete verwalten**.  Weitere Informationen zu NuGet und Hinzufügen von NuGet-Pakete, finden Sie unter [NuGet-Übersicht](http://docs.nuget.org/) und [Verwalten von NuGet-Paketen mithilfe des Dialogfelds](http://docs.nuget.org/Consume/Package-Manager-Dialog).  
  
3. Suchen Sie nach VSIXSignTool aus VisualStudioExtensibility, und installieren Sie das NuGet-Paket.  
  
4. Sie können jetzt die VSIXSignTool von Lokale Pakete-Speicherort des Projekts ausführen. Wenden Sie sich an das Tool die Befehlszeilenhilfe für Ihr Szenario signieren (VSIXSignTool.exe /?).  
  
   Zum Beispiel können Sie mit einem Kennwort geschützte Zertifikatdatei signieren:  
  
   VSIXSignTool.exe anmelden/f \<Certfile >/p \<Kennwort > \<VSIXfile >  
  
## <a name="see-also"></a>Siehe auch  
 [Bereitstellen von Visual Studio-Erweiterungen](../extensibility/shipping-visual-studio-extensions.md)

