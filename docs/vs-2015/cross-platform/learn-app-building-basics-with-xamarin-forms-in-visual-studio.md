---
title: Erlernen von Grundlagen der App-Erstellung mit Xamarin.Forms in Visual Studio | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d22b5186-9e03-4e85-afc9-7cbe28522a6d
caps.latest.revision: 14
ms.author: crdun
manager: crdun
ms.openlocfilehash: 0defd7d3500f15726a26b9d42e4b768fa09a083c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51792059"
---
# <a name="learn-app-building-basics-with-xamarinforms-in-visual-studio"></a>Erlernen von Grundlagen der App-Erstellung mit Xamarin.Forms in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Nachdem Sie die Schritte in [Setup and install](../cross-platform/setup-and-install.md) und [Verify your Xamarin environment](../cross-platform/verify-your-xamarin-environment.md)ausgeführt haben, veranschaulicht diese exemplarische Vorgehensweise das Erstellen einer einfachen App (siehe unten) mit Xamarin.Forms. Mit Xamarin.Forms wird Ihr gesamter UI-Code einmal in eine portable Klassenbibliothek (portable class library; PCL) geschrieben. Xamarin rendert dann automatisch die nativen UI-Steuerelemente für iOS-, Android- und Windows-Plattformen. Dieser Ansatz wird empfohlen, da die PCL-Option am besten die Verwendung nur derjenigen .NET-APIs unterstützt, die auf allen Zielplattformen unterstützt werden, und da Xamarin.Forms plattformübergreifend die gemeinsame Nutzung des UI-Codes ermöglicht.  
  
 ![Das Beispiel für die WeatherApp unter Android, iOS und Windows Phone](../cross-platform/media/crossplat-xamarin-formsguide-1.png "CrossPlat Xamarin FormsGuide 1")  
  
 Zum Erstellen müssen Sie die folgenden Schritte ausführen:  
  
-   [Einrichten der Projektmappe](#solution)  
  
-   [Schreiben von freigegebenem Datendienstcode](#dataservice)  
  
-   [Schreiben von freigegebenem Benutzeroberflächencode](#uicode)  
  
-   [Testen der App mit dem Visual Studio-Emulator für Android](#test)  
  
-   [Fertigstellen der Benutzeroberfläche mit einem homogenen Aussehen und Verhalten über Plattformen hinweg](#finish)  
  
> [!TIP]
>  Den vollständigen Quellcode dieses Projekts finden Sie im [Repository „xamarin-forms-samples“ auf GitHub](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather).  
  
##  <a name="solution"></a> Einrichten der Projektmappe  
 Mit diesen Schritten erstellen Sie eine Xamarin.Forms-Projektmappe, die eine PCL für freigegebenen Code und zwei zusätzliche NuGet-Pakete enthält.  
  
1.  Erstellen Sie in Visual Studio eine neue **Leere App (Xamarin.Forms Portable)** -Projektmappe, und benennen Sie diese **WeatherApp**. Sie finden diese Vorlage am einfachsten, indem Sie **Xamarin.Forms** in das Suchfeld eingeben.  
  
     Wenn Sie sie dort nicht finden, müssen Sie möglicherweise Xamarin installieren oder das Visual Studio 2015-Feature aktivieren, wie unter [Setup und Installation](../cross-platform/setup-and-install.md) beschrieben.  
  
     ![Erstellen einer neuen leeren App &#40;Xamarin.Forms Portable&#41; Projekt](../cross-platform/media/crossplat-xamarin-formsguide-2.png "CrossPlat Xamarin FormsGuide 2")  
  
2.  Nachdem Sie auf „OK“ geklickt haben, um die Projektmappe zu erstellen, verfügen Sie über eine Reihe einzelner Projekte:  
  
    -   **WeatherApp (Portable)**: die PCL, in die Sie Code schreiben, der plattformübergreifend freigegeben wird, einschließlich allgemeiner Geschäftslogik und UI-Code, die mit Xamarin.Forms verwendet werden.  
  
    -   **WeatherApp.Droid**: das Projekt, das den systemeigenen Android-Code enthält. Dieses wird als Standardstartprojekt festgelegt.  
  
    -   **WeatherApp.iOS**: das Projekt, das den systemeigenen iOS-Code enthält.  
  
    -   **WeatherApp.UWP**: das Projekt, das Windows 10 UWP-Code enthält.  
  
    -   **WeatherApp.Windows (Windows 8.1)**: das Projekt, das nativen Windows 8.1-Code enthält.  
  
    -   **WeatherApp.WinPhone (Windows Phone 8.1)**: das Projekt, das den nativen Phone-Code enthält.  
  
    > [!NOTE]
    >  Natürlich können Sie die Projekte für Plattformen löschen, die Sie nicht als Zielplattform vorgesehen haben. Im Rahmen dieser exemplarischen Vorgehensweise beziehen wir uns auf die Android-, iOS- und Windows Phone 8.1-Projekte. Das Arbeiten mit den UWP- und Windows 8.1-Projekten ist dem Arbeiten mit dem Windows Phone 8.1-Projekt sehr ähnlich.  
  
     Innerhalb eines systemeigenen Projekts haben Sie Zugriff auf den systemeigenen Designer für die entsprechende Plattform und können nach Bedarf plattformspezifische Bildschirme und Funktionen implementieren.  
  
3.  Aktualisieren Sie das Xamarin.Forms-NuGet-Paket in der Projektmappe wie folgt auf die neueste stabile Version. Diese Schritte, sollten immer dann ausgeführt werden, wenn Sie eine neue Xamarin-Projektmappe erstellen:  
  
    -   Wählen Sie **Tools > NuGet-Paket-Manager > NuGet-Pakete für Projektmappe verwalten** aus.  
  
    -   Aktivieren Sie auf der Registerkarte **Updates** das **Xamarin.Forms** -Update für alle Projekte in der Projektmappe. (Hinweis: Lassen Sie alle Updates für Xamarin.Android.Support deaktiviert.)  
  
    -   Aktualisieren Sie das Feld **Version** auf die **neueste stabile** Version, die verfügbar ist.  
  
    -   Klicken Sie auf **Aktualisieren**.  
  
         ![Aktualisieren des Xamarin.Forms NuGet-Pakets](../cross-platform/media/crossplat-xamarin-formsguide-4.png "CrossPlat Xamarin FormsGuide 4")  
  
4.  Fügen Sie das NuGet-Paket **Newtonsoft.Json** zum PCL-Projekt hinzu, das Sie zum Verarbeiten der von einem Wetterdatendienst abgerufenen Informationen verwenden:  
  
    -   Wählen Sie im (aus Schritt 3 noch geöffneten) NuGet-Paket-Manager die Registerkarte **Durchsuchen** aus, und suchen Sie nach **Newtonsoft**.  
  
    -   Wählen Sie **Newtonsoft.Json**aus.  
  
    -   Aktivieren Sie das **WeatherApp** -Projekt (das einzige Projekt, in dem Sie das Paket installieren müssen).  
  
    -   Stellen Sie sicher, dass das **Version** -Feld auf die **neueste stabile** Version festgelegt ist.  
  
    -   Klicken Sie auf **Installieren**.  
  
    -   ![Suchen und Installieren des Newtonsoft.Json NuGet-Pakets](../cross-platform/media/crossplat-xamarin-formsguide-5.png "CrossPlat Xamarin FormsGuide 5")  
  
5.  Wiederholen Sie Schritt 4, um das **Microsoft.Net.Http** -Paket zu suchen und zu installieren.  
  
6.  Erstellen Sie die Projektmappe, und vergewissern Sie sich, dass keine Buildfehler aufgetreten sind.  
  
##  <a name="dataservice"></a> Schreiben von freigegebenem Datendienstcode  
 Im Projekt **WeatherApp (Portable)** schreiben Sie Code für die portable Klassenbibliothek (portable class library; PCL), die plattformübergreifend verwendet wird. Von iOS-, Android- und Windows Phone-Projekten erstellten App-Paketen wird die PCL automatisch hinzugefügt.  
  
 Registrieren Sie sich unter [http://openweathermap.org/appid](http://openweathermap.org/appid) für einen kostenlosen API-Schlüssel, um dieses Beispiel auszuführen.  
  
 Mit den folgenden Schritten wird Code zu der PCL hinzugefügt, um auf Daten von diesem Wetterdienst zuzugreifen und diese zu speichern:  
  
1.  Klicken Sie mit der rechten Maustaste auf das **WeatherApp**-Projekt, und wählen Sie **Hinzufügen > Klasse…** aus. Geben Sie der Datei im Dialogfeld **Neues Element hinzufügen** den Namen **Weather.cs**. Sie nutzen diese Klasse später, um Daten aus dem Wetterdatendienst zu speichern.  
  
2.  Ersetzen Sie den gesamten Inhalt von **Weather.cs** durch folgenden Code:  
  
    ```csharp  
    namespace WeatherApp  
    {  
        public class Weather  
        {  
            public string Title { get; set; }  
            public string Temperature { get; set; }  
            public string Wind { get; set; }  
            public string Humidity { get; set; }  
            public string Visibility { get; set; }  
            public string Sunrise { get; set; }  
            public string Sunset { get; set; }  
  
            public Weather()  
            {  
                //Because labels bind to these values, set them to an empty string to  
                //ensure that the label appears on all platforms by default.  
                this.Title = " ";  
                this.Temperature = " ";  
                this.Wind = " ";  
                this.Humidity = " ";  
                this.Visibility = " ";  
                this.Sunrise = " ";  
                this.Sunset = " ";  
            }  
        }  
    }  
    ```  
  
3.  Fügen Sie eine weitere Klasse zum PCL-Projekt namens **DataService.cs** hinzu, die Sie zum Verarbeiten von JSON-Daten aus dem Wetterdatendienst verwenden.  
  
4.  Ersetzen Sie den gesamten Inhalt von **DataService.cs** durch folgenden Code:  
  
    ```csharp  
    using System.Threading.Tasks;  
    using Newtonsoft.Json;  
    using System.Net.Http;  
  
    namespace WeatherApp  
    {  
        public class DataService  
        {  
            public static async Task<dynamic> getDataFromService(string queryString)  
            {  
                HttpClient client = new HttpClient();  
                var response = await client.GetAsync(queryString);  
  
                dynamic data = null;  
                if (response != null)  
                {  
                    string json = response.Content.ReadAsStringAsync().Result;  
                    data = JsonConvert.DeserializeObject(json);  
                }  
  
                return data;  
            }  
        }  
    }  
    ```  
  
5.  Fügen Sie der PCL eine dritte Klasse hinzu, und nennen Sie diese **Core** . Darin wird die freigegebene Geschäftslogik abgelegt, z.B. Logik, die mithilfe einer Postleitzahl eine Abfragezeichenfolge bildet, den Wetterdatendienst aufruft und anschließend eine Instanz der **Weather** -Klasse auffüllt.  
  
6.  Ersetzen Sie den Inhalt von **Core.cs** durch folgenden Code:  
  
    ```csharp  
    using System;  
    using System.Threading.Tasks;  
  
    namespace WeatherApp  
    {  
        public class Core  
        {  
            public static async Task<Weather> GetWeather(string zipCode)  
            {  
                //Sign up for a free API key at http://openweathermap.org/appid  
                string key = "YOUR KEY HERE";  
                string queryString = "http://api.openweathermap.org/data/2.5/weather?zip="  
                    + zipCode + ",us&appid=" + key + "&units=imperial";  
  
                dynamic results = await DataService.getDataFromService(queryString).ConfigureAwait(false);  
  
                if (results["weather"] != null)  
                {  
                    Weather weather = new Weather();  
                    weather.Title = (string)results["name"];                  
                    weather.Temperature = (string)results["main"]["temp"] + " F";  
                    weather.Wind = (string)results["wind"]["speed"] + " mph";                  
                    weather.Humidity = (string)results["main"]["humidity"] + " %";  
                    weather.Visibility = (string)results["weather"][0]["main"];  
  
                    DateTime time = new System.DateTime(1970, 1, 1, 0, 0, 0, 0);  
                    DateTime sunrise = time.AddSeconds((double)results["sys"]["sunrise"]);  
                    DateTime sunset = time.AddSeconds((double)results["sys"]["sunset"]);  
                    weather.Sunrise = sunrise.ToString() + " UTC";  
                    weather.Sunset = sunset.ToString() + " UTC";  
                    return weather;  
                }  
                else  
                {  
                    return null;  
                }  
            }  
        }  
    }  
    ```  
  
7.  Erstellen Sie das PCL-Projekt **WeatherApp** , um sicherzustellen, dass der Code korrekt ist.  
  
##  <a name="uicode"></a> Schreiben von freigegebenem Benutzeroberflächencode  
 Mit Xamarin.Forms können Sie freigegebenen Benutzeroberflächencode in der PCL implementieren. Mit den folgenden Schritten fügen Sie zur PCL einen Bildschirm mit einer Schaltfläche hinzu, deren Text mit den Daten aktualisiert wird, die von dem im vorherigen Abschnitt hinzugefügten Wetterdatendienst-Code zurückgegeben werden:  
  
1.  Fügen Sie eine **Forms Xaml Page** mit dem Namen **WeatherPage.cs** hinzu, indem Sie mit der rechten Maustaste auf das **WeatherApp**-Projekt klicken und **Hinzufügen > Neues Element...** auswählen. Suchen Sie im Dialogfeld **Neues Element hinzufügen** nach „Forms“, wählen Sie **Forms Xaml Page**, und nennen Sie sie **WeatherPage.cs**.  
  
     Xamarin.Forms ist XAML-basiert, daher wird mit diesem Schritt eine **WeatherPage.xaml** -Datei zusammen mit der geschachtelten CodeBehind-Datei **WeatherPage.xaml.cs**erstellt. Dadurch können Sie die Benutzeroberfläche entweder über XAML oder Code generieren. In dieser exemplarischen Vorgehensweise werden Teile beide Methoden verwendet.  
  
     ![Hinzufügen einer neuen Seite für Xamarin.Forms XAML](../cross-platform/media/crossplat-xamarin-formsguide-6.png "CrossPlat Xamarin FormsGuide 6")  
  
2.  Um eine Schaltfläche zum WeatherPage-Bildschirm hinzuzufügen, ersetzen Sie den Inhalt von „WeatherPage.xaml“ durch folgenden Code:  
  
    ```xaml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <ContentPage xmlns="http://xamarin.com/schemas/2014/forms"  
           xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"  
           x:Class="WeatherApp.WeatherPage">  
      <Button x:Name="getWeatherBtn" Text="Get Weather"/>  
    </ContentPage>  
    ```  
  
     Beachten Sie, dass der Name der Schaltfläche mit dem **:Name** -Attribut definiert werden muss, sodass Sie aus der CodeBehind-Datei heraus anhand des Namens auf diese Schaltfläche verweisen können.  
  
3.  Um einen Ereignishandler für das **Clicked** -Ereignis der Schaltfläche hinzufügen, um den Text der Schaltfläche zu aktualisieren, ersetzen Sie den Inhalt von **WeatherPage.xaml.cs** durch den unten stehenden Code. (Sie können „60601“ natürlich in eine andere Postleitzahl ändern.)  
  
    ```csharp  
    using System;  
    using Xamarin.Forms;  
  
    namespace WeatherApp  
    {  
        public partial class WeatherPage: ContentPage  
        {  
            public WeatherPage()  
            {  
                InitializeComponent();  
                this.Title = "Sample Weather App";  
                getWeatherBtn.Clicked += GetWeatherBtn_Clicked;  
  
                //Set the default binding to a default object for now  
                this.BindingContext = new Weather();  
            }  
  
            private async void GetWeatherBtn_Clicked(object sender, EventArgs e)  
            {  
                Weather weather = await Core.GetWeather("60601");  
                getWeatherBtn.Text = weather.Title;  
            }  
        }  
    }  
    ```  
  
4.  Um **WeatherPage** als ersten Bildschirm beim Starten der App zu öffnen, ersetzen Sie den Standardkonstruktor in **App.cs** durch den folgenden Code:  
  
    ```csharp  
    public App()  
    {  
        MainPage = new NavigationPage(new WeatherPage());  
    }  
    ```  
  
5.  Erstellen Sie das PCL-Projekt „WeatherApp“, um sicherzustellen, dass der Code korrekt ist.  
  
##  <a name="test"></a> Testen der App mit dem Visual Studio-Emulator für Android  
 Nun können Sie die App ausführen. Führen Sie zunächst nur die Android-Version aus, um zu überprüfen, ob die App Daten vom den Wetterdienst empfängt. Später, nachdem Sie weitere Benutzeroberflächenelemente hinzugefügt haben, führen Sie auch die iOS- und die Windows Phone-Versionen aus. (Hinweis: Wenn Sie Visual Studio unter Windows 7 ausführen, führen Sie dieselben Schritte aus, verwenden aber stattdessen den Xamarin Player.)  
  
1.  Legen Sie das **WeatherApp.Droid** -Projekt als Startprojekt fest, indem Sie mit der rechten Maustaste darauf klicken und **Als Startprojekt festlegen**auswählen.  
  
2.  In der Visual Studio-Symbolleiste ist **WeatherApp.Droid** als Zielprojekt aufgeführt. Wählen Sie einen der Android-Emulatoren für das Debuggen aus, und drücken Sie **F5**. Es empfiehlt sich die Verwendung einer der **VS-Emulator** -Optionen, die die App im Visual Studio-Emulator für Android ausführen.  
  
     ![Debug-Ziel für VS-Emulator auswählen](../cross-platform/media/crossplat-xamarin-formsguide-7.png "CrossPlat Xamarin FormsGuide 7")  
  
3.  Wenn die App im Emulator gestartet wird, klicken Sie auf die **Wetter abrufen** -Schaltfläche. Der Text der Schaltfläche sollte zu **Chicago, IL**geupdatet werden, was die Eigenschaft *Title* der beim Wetterdatendienst abgerufenen Daten ist.  
  
     ![WeatherApp vor und nach dem Tippen der Schaltfläche](../cross-platform/media/crossplat-xamarin-formsguide-8.png "CrossPlat Xamarin FormsGuide 8")  
  
##  <a name="finish"></a> Fertigstellen der Benutzeroberfläche mit einem plattformübergreifenden, nativen Aussehen und Verhalten  
 Xamarin.Forms rendert systemeigene Benutzeroberflächen-Steuerelemente für jede Plattform, damit die App automatisch ein homogenes Aussehen und Verhalten aufweist. Um dies besser zu verdeutlichen, stellen Sie die Benutzeroberfläche mit einem Eingabefeld für eine Postleitzahl festig, und zeigen Sie dann die Wetterdaten an, die vom Dienst zurückgegeben werden.  
  
1. Ersetzen Sie den Inhalt von **WeatherPage.xaml** durch den unten stehenden Code. Beachten Sie, dass jedes Element, wie zuvor beschrieben, mit dem **x:Name** -Attribut benannt wird, damit vom Code aus auf das Element verwiesen werden kann. Xamarin.Forms stellt außerdem eine Reihe von [Layoutoptionen](http://developer.xamarin.com/guides/xamarin-forms/controls/layouts/) (xamarin.com) bereit. Hier verwendet WeatherPage [StackLayout](http://developer.xamarin.com/api/type/Xamarin.Forms.StackLayout/) (xamarin.com).  
  
   ```xaml  
   <?xml version="1.0" encoding="utf-8" ?>  
   <ContentPage xmlns="http://xamarin.com/schemas/2014/forms"  
          xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"  
          x:Class="WeatherApp.WeatherPage">  
  
     <ContentPage.Resources>  
       <ResourceDictionary>  
         <Style x:Key="labelStyle" TargetType="Label">  
           <Setter Property="TextColor" Value="#a8a8a8" />  
           <Setter Property="FontSize" Value="Small" />  
         </Style>  
         <Style x:Key="fieldStyle" TargetType="Label">  
           <Setter Property="TextColor">  
             <OnPlatform x:TypeArguments="Color" iOS="Black" Android="White" WinPhone="White" />  
           </Setter>  
           <Setter Property="FontSize" Value="Medium" />  
         </Style>  
         <Style x:Key="fieldView" TargetType="ContentView">  
           <Setter Property="Padding" Value="10,0,0,0" />  
         </Style>  
       </ResourceDictionary>  
     </ContentPage.Resources>  
  
     <ContentPage.Content>  
       <ScrollView>  
         <StackLayout>  
           <StackLayout Orientation="Horizontal" HorizontalOptions="FillAndExpand"  
                 BackgroundColor="#545454">  
             <StackLayout Padding="10,10,10,10" HorizontalOptions="Start">  
               <Label Text="Search by Zip Code" TextColor="White" FontAttributes="Bold"  
                   FontSize="Medium" />  
               <Label x:Name="zipCodeLabel" Text="Zip Code" Style="{StaticResource labelStyle}" />  
               <Entry x:Name="zipCodeEntry" />  
             </StackLayout>  
             <StackLayout Padding="0,0,0,10" VerticalOptions="End">  
               <Button x:Name="getWeatherBtn" Text="Get Weather" WidthRequest="185" BorderWidth="1" >  
                 <!-- Set iOS colors; use defaults on other platforms -->  
                 <Button.TextColor>  
                   <OnPlatform x:TypeArguments="Color" iOS="White"/>  
                 </Button.TextColor>  
                 <Button.BorderColor>  
                   <OnPlatform x:TypeArguments="Color" iOS="White"/>  
                 </Button.BorderColor>  
               </Button>  
             </StackLayout>  
           </StackLayout>  
           <StackLayout Padding="10,10,10,10" HorizontalOptions="Start">  
             <Label Text="Location" Style="{StaticResource labelStyle}" />  
             <ContentView Style="{StaticResource fieldView}">  
               <Label Text="{Binding Title}" Style="{StaticResource fieldStyle}" />  
             </ContentView>  
             <Label Text="Temperature" Style="{StaticResource labelStyle}" />  
             <ContentView Style="{StaticResource fieldView}">  
               <Label x:Name="tempLabel" Text="{Binding Temperature}"  
                   Style="{StaticResource fieldStyle}" />  
             </ContentView>  
             <Label Text="Wind Speed" Style="{StaticResource labelStyle}" />  
             <ContentView Style="{StaticResource fieldView}">  
               <Label x:Name="windLabel" Text="{Binding Wind}" Style="{StaticResource fieldStyle}" />  
             </ContentView>  
             <Label Text="Humidity" Style="{StaticResource labelStyle}" />  
             <ContentView Style="{StaticResource fieldView}">  
               <Label x:Name="humidityLabel" Text="{Binding Humidity}"  
                   Style="{StaticResource fieldStyle}" />  
             </ContentView>  
             <Label Text="Visibility" Style="{StaticResource labelStyle}" />  
             <ContentView Style="{StaticResource fieldView}">  
               <Label x:Name="visibilitylabel" Text="{Binding Visibility}"  
                   Style="{StaticResource fieldStyle}" />  
             </ContentView>  
             <Label Text="Time of Sunrise" Style="{StaticResource labelStyle}" />  
             <ContentView Style="{StaticResource fieldView}">  
               <Label x:Name="sunriseLabel" Text="{Binding Sunrise}"  
                   Style="{StaticResource fieldStyle}" />  
             </ContentView>  
             <Label Text="Time of Sunset" Style="{StaticResource labelStyle}" />  
             <ContentView Style="{StaticResource fieldView}">  
               <Label x:Name="sunsetLabel" Text="{Binding Sunset}"  
                   Style="{StaticResource fieldStyle}" />  
             </ContentView>  
           </StackLayout>  
         </StackLayout>  
       </ScrollView>  
     </ContentPage.Content>  
   </ContentPage>  
   ```  
  
    Beachten Sie die Verwendung des Tags **OnPlatform** in Xamarin.Forms. **OnPlatform** wählt einen Eigenschaftswert aus, der spezifisch für die Plattform ist, auf der die App aktuell ausgeführt wird (siehe [Essential XAML Syntax](http://developer.xamarin.com/guides/xamarin-forms/user-interface/xaml-basics/essential_xaml_syntax/) („Essentielle XAML-Syntax“ auf xamarin.com). Das Tag wird hier verwendet, um für die Datenfelder eine andere Farbe festzulegen: Weiß unter Android und Windows Phone, Schwarz unter iOS. Sie können **OnPlatform** für alle Eigenschaften und alle Datentypen verwenden, um an einer beliebigen Stelle in XAML-Code plattformspezifische Anpassungen vorzunehmen. In der CodeBehind-Datei dient die [Device.OnPlatform-API](http://developer.xamarin.com/guides/xamarin-forms/platform-features/device/) demselben Zweck.  
  
2. Ersetzen Sie in **WeatherPage.xaml.cs**den **GetWeatherBtn_Clicked** -Ereignishandler durch den unten stehenden Code. Mit diesem Code wird überprüft, ob im Eingabefeld eine Postleitzahl angegeben wurde. Anschließend werden Daten für diese Postleitzahl abgerufen, der Bindungskontext für den gesamten Bildschirm wird auf die resultierende Weather-Instanz festgelegt, und abschließend wird der Schaltflächentext in „Erneut suchen“ geändert. Beachten Sie, dass jede Bezeichnung in der Benutzeroberflächen an eine Eigenschaft der Klasse „Weather“ gebunden ist. Wenn Sie also den Bindungskontext des Bildschirms auf eine **Weather** -Instanz festlegen, werden diese Bezeichnungen automatisch aktualisiert.  
  
   ```csharp  
   private async void GetWeatherBtn_Clicked(object sender, EventArgs e)  
   {  
       if (!String.IsNullOrEmpty(zipCodeEntry.Text))  
       {  
           Weather weather = await Core.GetWeather(zipCodeEntry.Text);  
           this.BindingContext = weather;  
           getWeatherBtn.Text = "Search Again";  
       }  
   }  
   ```  
  
3. Führen Sie die App auf allen drei Plattformen (Android, iOS und Windows Phone) aus, indem Sie mit der rechten Maustaste auf das entsprechende Projekt klicken, die Option „Als Startprojekt festlegen“ auswählen und die App entweder auf einem Gerät oder im Emulator bzw. Simulator starten. Geben Sie eine gültige US-Postleitzahl ein (z. B. 60601), und klicken Sie auf die Schaltfläche „Wetter abrufen“, um, wie unten dargestellt, Wetterdaten für diese Region anzuzeigen. Selbstverständlich muss Visual Studio mit einem Mac OS X-Computer in Ihrem Netzwerk für das iOS-Projekt verbunden sein.  
  
    ![Das Beispiel für die WeatherApp unter Android, iOS und Windows Phone](../cross-platform/media/crossplat-xamarin-formsguide-1.png "CrossPlat Xamarin FormsGuide 1")  
  
   Der vollständige Quellcode dieses Projekts befindet sich im [Repository „xamarin-forms-samples“ auf GitHub](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather).

