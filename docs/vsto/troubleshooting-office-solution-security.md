---
title: Behandeln von Problemen mit der Sicherheit von Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], troubleshooting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 289ffc3b5260260c9da8d0ec61e5c79890394802
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985564"
---
# <a name="troubleshoot-office-solution-security"></a>Behandeln von Problemen mit der Sicherheit von Office
  Dieses Thema enthält Tipps zum Lösen allgemeiner Probleme, die bei der Arbeit mit dem Sichern von Office-Lösungen auftreten können.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trusted-solutions-cannot-be-installed-from-restricted-sites"></a>Vertrauenswürdige Lösungen können nicht von eingeschränkten Sites installiert werden.
 Benutzer können eine Lösung nicht von einem Webspeicherort installieren, wenn die Website in der Zone Eingeschränkte Sites von Internet Explorer aufgeführt ist. Dies gilt auch, wenn die Lösung mit einem vertrauenswürdigen Zertifikat signiert ist.

 Die URL des Bereitstellungs Manifests kann in eine von fünf Zonen kategorisiert werden:

- Arbeitsplatz

- Internet

- Lokales Intranet

- Vertrauenswürdige Sites

- Eingeschränkte Websites

  Wenn der Speicherort des Bereitstellungs Manifests der Zone der eingeschränkten Sites zugewiesen wurde, wird die Lösung von [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] nicht installiert. Wenn der Speicherort bekannt ist und als vertrauenswürdig eingestuft werden kann, kann der Benutzer den Speicherort aus der Zone der eingeschränkten Sites entfernen und die Lösung installieren. Informationen zum Verwalten von Zonen finden Sie unter [Konfigurieren von ClickOnce-vertrauenswürdigen Verlegern](/previous-versions/dotnet/articles/ms996418(v=msdn.10)).

## <a name="solutions-cannot-be-installed-from-network-file-shares-or-web-locations-when-internet-explorer-enhanced-security-configuration-or-internet-explorer-7-is-installed"></a>Lösungen können nicht von Netzwerkdatei Freigaben oder webstandorten aus installiert werden, wenn die verstärkte Sicherheitskonfiguration für Internet Explorer oder Internet Explorer 7 installiert ist.
 Durch die verstärkte Sicherheitskonfiguration für Internet Explorer (IEESC) in Windows Server 2003 und höher sowie Internet Explorer 7 und höher wird die Möglichkeit der Benutzer das Durchsuchen des Internets erheblich eingeschränkt. Wenn Benutzer versuchen, Office-Projektmappen über eine Netzwerkdatei Freigabe oder einen Webspeicherort zu installieren, erhalten Sie möglicherweise die folgende Fehlermeldung: "die angepasste Funktionalität in dieser Anwendung funktioniert nicht, da das Zertifikat zum Signieren des Bereitstellungs Manifests für *verwendet wird. SolutionName* ist nicht vertrauenswürdig. Wenden Sie sich für weitere Unterstützung an Ihren Administrator. "

 Wenn bei IEESC und Internet Explorer 7 und höher die URL des Bereitstellungs Manifests in der Zone "Internet" kategorisiert wird, muss das Manifest über ein Zertifikat von einem vertrauenswürdigen Herausgeber verfügen, oder die Lösung kann nicht installiert werden. Ohne IEESC ist das Standardverhalten, den Endbenutzer aufzufordern, eine Vertrauens Entscheidung zu treffen.

 Um die Auswirkungen von IEESC und Internet Explorer 7 und höher zu verwalten, identifizieren Sie Websites und UNC-Pfade (Universal Naming Convention), denen Sie Vertrauen, und fügen Sie Sie einer vertrauenswürdigen Sicherheitszone (Lokales Intranet oder Vertrauenswürdige Sites) hinzu. Weitere Informationen zum Verwalten von Zonen finden Sie unter [Konfigurieren von ClickOnce-vertrauenswürdigen Verlegern](/previous-versions/dotnet/articles/ms996418(v=msdn.10)).

## <a name="see-also"></a>Siehe auch
- [Sichere Office-Lösungen](../vsto/securing-office-solutions.md)
