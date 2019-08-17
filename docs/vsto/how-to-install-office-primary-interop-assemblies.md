---
title: 'Vorgehensweise: Installieren von primären Interopassemblys für Office'
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- primary interop assemblies [Office development in Visual Studio], installing
- Office primary interop assemblies, installing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ee6755a2d795d2018136785986a5a346ddc07dc6
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551797"
---
# <a name="how-to-install-office-primary-interop-assemblies"></a>Vorgehensweise: Installieren von primären Interopassemblys für Office
  Installieren Sie die primären Interop-Assemblys (PIAs) für Microsoft Office bei der Installation von Office.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="to-install-the-pias-when-you-install-office"></a>Zum Installieren der PIAs bei der Installation von Office

1. Stellen Sie sicher, dass Sie über eine Version von .NET Framework verfügen, die nicht älter als Version 2.0 ist.

2. Installieren Sie Microsoft Office, und stellen Sie sicher, dass die Funktion **.net-Programmier Unterstützung** für die Anwendungen ausgewählt ist, die Sie erweitern möchten (dieses Feature ist in der Standardinstallation enthalten).

    > [!WARNING]
    > In der Standardeinstellung werden die PIA in Ihre Lösung eingebettet, wenn Sie Sie erstellen, damit Sie PIAs nicht als Voraussetzung für die Verwendung des VSTO-Add-Ins oder der Anpassung an Benutzer verteilen müssen.

## <a name="see-also"></a>Siehe auch
- [Primäre Interopassemblys für Office](../vsto/office-primary-interop-assemblies.md)
- [Vorgehensweise: Abzielen von Office-Anwendungen über primäre Interopassemblys](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Vorgehensweise: Konfigurieren eines Computers zum Entwickeln von Office-Projektmappen](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)
- [Vorgehensweise: Installieren des Visual Studio-Tools für die weitervertreibbare Office-Laufzeit](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)
- [Übersicht über &#40;die Entwicklung von Office-Lösungen VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Einstieg in &#40;die Office-Entwicklung in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
