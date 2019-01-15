---
title: 'Vorgehensweise: Angeben der .NET Framework-Laufzeit | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools, .NET Framework versions
- .NET Framework versions,profililng
ms.assetid: d39f3579-719a-4f47-a97d-5b4232fe4c64
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 6baa0e37acb4ba24d0622ad27fe84c47e84da59d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53911012"
---
# <a name="how-to-specify-the-net-framework-runtime"></a>Vorgehensweise: Angeben der .NET Framework-Laufzeit

Mit der Veröffentlichung von [!INCLUDE[net_v40_long](../code-quality/includes/net_v40_long_md.md)] können Anwendungen mit Modulen zusammengesetzt sein, die mit verschiedenen Versionen der [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]-Laufzeit erstellt wurden. Standardmäßig erstellen die Visual Studio-Profilerstellungstools für die erste Laufzeit, die von der Anwendung geladen wird, ein Profil. Sie können die Laufzeit zur Profilerstellung angeben, wenn Sie eine Anwendung mit dem Profiler starten, und wenn Sie den Profiler an eine bereits ausgeführte Anwendung anfügen.

## <a name="to-specify-the-net-framework-run-time-to-profile-when-starting-an-application-with-the-profiler"></a>So geben Sie die .NET Framework-Laufzeit, für die ein Profil erstellt werden soll, beim Starten einer Anwendung über den Profiler an

1. Klicken Sie im **Leistungs-Explorer** mit der rechten Maustaste auf die Leistungssitzung, nun auf **Eigenschaften** und anschließend auf **Erweitert**.

     Das Listenfeld **Ziel-CLR-Version** zeigt **Automatisch** und die Versionen der [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]-Laufzeit an, die auf dem Computer installiert sind.

2. Führen Sie einen der folgenden Schritte aus:

    - Klicken Sie auf die Version der CLR, für die Sie ein Profil erstellen möchten.

    - Klicken Sie auf **Automatisch**, um für die erste Version, die von der Anwendung geladen wird, ein Profil zu erstellen.

## <a name="to-specify-the-net-framework-run-time-to-profile-when-attaching-the-profiler-to-an-application"></a>So geben Sie die .NET Framework-Laufzeit, für die ein Profil erstellt werden soll, beim Anfügen des Profilers an eine Anwendung an

1. Zeigen Sie m Menü **Analysieren** auf **Profiler**, und klicken Sie anschließend auf **Anfügen/Trennen**.

2. Klicken Sie im Dialogfeld **Profiler an Prozess anfügen** auf den Prozess, für den Sie ein Profil erstellen möchten.

     Das Listenfeld **Ziel-CLR-Version** zeigt **Automatisch** und die Versionen der [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]-Laufzeit an, die auf dem Computer installiert sind.

3. Führen Sie einen der folgenden Schritte aus:

    - Klicken Sie auf die Version der CLR, für die Sie ein Profil erstellen möchten.

    - Klicken Sie auf **Automatisch**, um für die Version ein Profil zu erstellen, die geladen wird, wenn der Profiler an die Anwendung angefügt wird.