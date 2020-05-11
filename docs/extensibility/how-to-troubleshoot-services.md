---
title: 'Gewusst wie: Troubleshoot Services | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, troubleshooting
ms.assetid: 001551da-4847-4f59-a0b2-fcd327d7f5ca
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 49560acdf57f5dad2c57f2a8e4649f194d6d8298
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710750"
---
# <a name="how-to-troubleshoot-services"></a>Gewusst wie: Fehlerbehebungsdienste
Es gibt mehrere häufige Probleme, die auftreten können, wenn Sie versuchen, einen Dienst abzubekommen:

- Der Dienst ist [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]nicht bei registriert.

- Der Dienst wird nach Schnittstellentyp und nicht nach Diensttyp angefordert.

- Das VSPackage, das den Dienst anfordert, wurde nicht standortseither eingerichtet.

- Es wird der falsche Dienstanbieter verwendet.

  Wenn der angeforderte Dienst nicht <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> abgerufen werden kann, wird der Aufruf von null zurückgegeben. Sie sollten immer auf NULL testen, nachdem Sie einen Dienst angefordert haben:

```csharp
IVsActivityLog log =
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;
if (log == null) return;
```

## <a name="to-troubleshoot-a-service"></a>So beheben Sie einen Dienst

1. Überprüfen Sie die Systemregistrierung, um festzustellen, ob der Dienst ordnungsgemäß registriert wurde. Weitere Informationen finden Sie unter [Gewusst wie: Bereitstellen eines Dienstes](../extensibility/how-to-provide-a-service.md).

    Das folgende *.reg-Dateifragment* zeigt, wie der SVsTextManager-Dienst registriert werden kann:

   ```
   [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]
   @="{F5E7E720-1401-11d1-883B-0000F87579D2}"
   "Name"="SVsTextManager"
   ```

    Im obigen Beispiel ist versionsnummer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]die Version von , z. B. 12.0 oder 14.0, der Schlüssel "F5E7E71D-1401-11d1-883B-0000F87579D2" ist die Dienstkennung (SID) des Dienstes, SVsTextManager und der Standardwert "F5E7E720-1401-11d1-883B-0000F87579D2" ist die Paket-GUID des Text-Managers VSPackage, der den Dienst bereitstellt.

2. Verwenden Sie den Diensttyp und nicht den Schnittstellentyp, wenn Sie GetService aufrufen. Beim Anfordern [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]eines <xref:Microsoft.VisualStudio.Shell.Package> Dienstes aus extrahiert die GUID aus dem Typ. Ein Dienst wird nicht gefunden, wenn die folgenden Bedingungen vorhanden sind:

   1. Anstelle des Diensttyps wird ein Schnittstellentyp an GetService übergeben.

   2. Der Schnittstelle ist keine GUID explizit zugewiesen. Daher erstellt das System bei Bedarf eine Standard-GUID für ein Objekt.

3. Stellen Sie sicher, dass das VSPackage, das den Dienst anfordert, standortseitfest eingerichtet wurde. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ein VSPackage nach dem Erstellen <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>und vor dem Aufruf von .

    Wenn Sie Code in einem VSPackage-Konstruktor haben, `Initialize` der einen Dienst benötigt, verschieben Sie ihn in die Methode.

4. Stellen Sie sicher, dass Sie den richtigen Dienstanbieter verwenden.

    Nicht alle Dienstleister sind gleich. Der Dienstanbieter, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] der an ein Toolfenster übergibt, unterscheidet sich von dem, das er an ein VSPackage übergibt. Der Toolfensterdienstanbieter kennt <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>, aber nicht <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>von . Sie können <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> aufrufen, um einen VSPackage-Dienstanbieter innerhalb eines Toolfensters abzurufen.

    Wenn ein Toolfenster ein Benutzersteuerelement oder einen anderen Steuerelementcontainer hostet, wird der Container vom [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Windows-Komponentenmodell erstellt und hat keinen Zugriff auf Dienste. Sie können <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> aufrufen, um einen VSPackage-Dienstanbieter innerhalb eines Steuerelementcontainers abzurufen.

## <a name="see-also"></a>Weitere Informationen
- [Liste der verfügbaren Dienste](../extensibility/internals/list-of-available-services.md)
- [Nutzung und Bereitstellung von Dienstleistungen](../extensibility/using-and-providing-services.md)
- [Service-Essentials](../extensibility/internals/service-essentials.md)
