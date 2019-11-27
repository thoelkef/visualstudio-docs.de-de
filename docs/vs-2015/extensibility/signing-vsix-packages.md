---
title: Signieren von VSIX-Paketen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b74222804e9ed42e6f8263cbe6ad0daf19cda81f
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300328"
---
# <a name="signing-vsix-packages"></a>Signieren von VSIX-Paketen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Erweiterungsassemblys müssen nicht signiert werden, bevor Sie in Visual Studio ausgeführt werden können. Dies ist jedoch eine bewährte Vorgehensweise.  
  
 Wenn Sie Ihre Erweiterung sichern und sicherstellen möchten, dass Sie nicht manipuliert wurde, können Sie einem VSIX-Paket eine digitale Signatur hinzufügen. Wenn eine VSIX signiert ist, zeigt das VSIX-Installationsprogramm eine Meldung mit dem Hinweis an, dass Sie signiert ist, sowie weitere Informationen zur Signatur selbst. Wenn die Inhalte der VSIX geändert wurden und die VSIX nicht erneut signiert wurde, zeigt das VSIX-Installationsprogramm an, dass die Signatur ungültig ist. Die Installation wird nicht beendet, aber der Benutzer ist gewarnt.  
  
> [!IMPORTANT]
> Ab 2015 werden VSIX-Pakete, die mit anderen als SHA256 Encryption signiert werden, als ungültige Signatur identifiziert. Die VSIX-Installation wird nicht blockiert, aber der Benutzer wird gewarnt.  
  
## <a name="signing-a-vsix-with-vsixsigntool"></a>Signieren einer VSIX mit vsixsigntool  
 Es gibt ein SHA256 Encryption-Signatur Tool, das unter " [visualstudioextensibility](https://www.nuget.org/profiles/VisualStudioExtensibility) " unter "nuget.org" unter [vsixsigntool](https://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool)verfügbar ist.  
  
#### <a name="to-use-the-vsixsigntool"></a>So verwenden Sie das vsixsigntool  
  
1. Fügen Sie die VSIX einem Projekt hinzu.  
  
2. Klicken Sie in Projektmappen-Explorer mit der rechten Maustaste auf den Projekt Knoten, und wählen **Sie &#124; nuget-Pakete verwalten**aus.  Weitere Informationen zu nuget und zum Hinzufügen von nuget-Paketen finden Sie unter [nuget: Übersicht](https://docs.microsoft.com/nuget/) und [Verwalten von nuget-Paketen mithilfe des Dialog](https://docs.microsoft.com/nuget/consume-packages/install-use-packages-visual-studio)Felds.  
  
3. Suchen Sie nach vsixsigntool aus visualstudioextensibility, und installieren Sie das nuget-Paket.  
  
4. Sie können jetzt das vsixsigntool aus dem lokalen Paket Speicherort des Projekts ausführen. Weitere Informationen zum Signier Szenario finden Sie in der Befehlszeilen Hilfe des Tools (vsixsigntool. exe/?).  
  
   So können Sie beispielsweise mit einer Kenn Wort geschützten Zertifikatsdatei signieren:  
  
   Vsixsigntool. exe Sign/f \<CertFile >/p \<Password > \<vsixfile >  
  
## <a name="see-also"></a>Siehe auch  
 [Bereitstellen von Visual Studio-Erweiterungen](../extensibility/shipping-visual-studio-extensions.md)
