
//============================================================================================================================================================
//+------------------------------------------------------------------+
//|            CHAVE SEGURANÇA TRAVA MENSAL PRO CLIENTE              |
//+------------------------------------------------------------------+
//============================================================================================================================================================
//demo DATA DA EXPIRAÇÃO                           // demo DATA DA EXPIRAÇÃO
bool use_demo= FALSE; // FALSE  // TRUE            // TRUE ATIVA / FALSE DESATIVA EXPIRAÇÃO
string ExpiryDate= "2024.12.09 00:00:00";                   // DATA DA EXPIRAÇÃO
string expir_msg="SAKIB KOMBINER EXPIRED CONTACT:@Sakib192010"; // MENSAGEM DE AVISO QUANDO EXPIRAR
//============================================================================================================================================================
//NÚMERO DA CONTA MT4                              // NÚMERO DA CONTA MT4
bool use_acc_number= TRUE ; // TRUE  // TRUE      // TRUE ATIVA / FALSE DESATIVA NÚMERO DE CONTA
long acc_number[]={220891737,16103749,1234775251,501247559,70415443,501258207};                        // NÚMERO DA CONTA
string acc_numb_msg="VERIFY ID!!! CONTACT:@Sakib192010"; //ID
//+------------------------------------------------------------------+
//|                        SAKIB KOMBINER                               |
//|                      Copyright 2024, SAKIB KOMBINER                 |
//|                  https://t.me/                                      |
//+------------------------------------------------------------------+

#property link        "https://t.me/SAKIBKOMBINERPRO"
#property description "DESIGNED BY SAKIB"
#property description "===================================="
#property description "Telegram Channel: https://t.me/SAKIBKOMBINERPRO"
#property description "Telegram Contact: @Sakib192010"
#property description "===================================="
#property description "Disclaimer: The developer assumes no responsibility for any gains or losses incurred from using this file."
#define EXAMPLE_PHOTO "\\Images\\@Sakib192010.bmp"
#property strict
//============================================================================================================================================================
#property indicator_chart_window
#property indicator_buffers 20
//============================================================================================================================================================
#include <WinUser32.mqh>

string SANXINDICATORPROTECTOR[256];

#import "user32.dll"
int   RegisterWindowMessageA(string lpstring);
int   PostMessageA(int  hWnd,int  Msg,int  wParam,string lParam);
#import
//-----------------------------------------------------------------------------------------------------------------------------------------------------------
#import "kernel32.dll"
int  FindFirstFileW(string Path, ushort &Answer[]);
bool FindNextFileW(int handle,  ushort &Answer[]);
bool FindClose(int handle);
#import



//============================================================================================================================================================
//============================================================================================================================================================
#import "Telegram4Mql.dll"
string TelegramSendText(string ApiKey, string ChatId, string ChatText);
string TelegramSendTextAsync(string apiKey, string chatId, string chatText);
string TelegramSendPhotoAsync(string apiKey, string chatId, string filePath, string caption = "");
#import

#import  "Wininet.dll"
int InternetOpenW(string, int, string, string, int);
int InternetConnectW(int, string, int, string, string, int, int, int);
int HttpOpenRequestW(int, string, string, int, string, int, string, int);
int InternetOpenUrlW(int, string, string, int, int, int);
int InternetReadFile(int, uchar & arr[], int, int& OneInt[]);
int InternetCloseHandle(int);
bool HttpSendRequestW(int, string, int, string, int);
#import

#import "Kernel32.dll"
   bool GetVolumeInformationW(string,string,uint,uint&[],uint,uint,string,uint);
   #import
//============================================================================================================================================================
//CORRETORAS DISPONÍVEIS
enum corretora_price_pro
  {
   EmTodas = 1,    //Todas
   EmIQOption = 2, //IQ Option
   EmSpectre = 3,  //Spectre
   EmBinary = 4,   //Binary
   EmGC = 5,       //Grand Capital
   EmBinomo = 6,   //Binomo
   EmOlymp = 7     //Olymp Trade
  };
//============================================================================================================================================================
enum broker
  {
   Todos = 0,   //Todas
   IQOption = 1,
   Binary = 2,
   Spectre = 3,
   Alpari = 4,
   InstaBinary = 5
  };
//============================================================================================================================================================
enum corretora
  {
   Todas = 0,   //Todas
   IQ = 1,      //IQ Option
   Bin = 2,     //Binary
   Spectree = 3,//Spectre
   GC = 4,      //Grand Capital
   Binomo = 5,  //Binomo
   Olymp = 6    //Olymp Trade
  };
//============================================================================================================================================================
enum sinal
  {
   MESMA_VELA = 0,  //SAME CANDLE
   PROXIMA_VELA = 1 //NEXT CANDLE
  };
//============================================================================================================================================================
enum tipo_expiracao
  {
   TEMPO_FIXO = 0, //Fixed Time!
   RETRACAO = 1    //Time Frame Time!
  };
//============================================================================================================================================================
enum entrar
  {
   NO_TOQUE = 0,    //NO TOQUE
   FIM_DA_VELA = 1  //FIM DA VELA
  };
//============================================================================================================================================================
enum modo
  {
   MELHOR_PAYOUT = 'M', //MELHOR PAYOUT
   BINARIAS = 'B',      //BINARIAS
   DIGITAIS = 'D'       //DIGITAIS
  };
//============================================================================================================================================================
enum instrument
  {
   DoBotPro= 3, //DO BOT PRO
   Binaria= 0,  //BINARIA
   Digital = 1, //DIGITAL
   MaiorPay =2  //MAIOR PAYOUT
  }; 
//============================================================================================================================================================
enum signaltype
  {
   IntraBar = 0,          // SAME CANDLE
   ClosedCandle = 1       // NEXT CANDLE
  };
//============================================================================================================================================================
enum martintype
  {
   NoMartingale = 0,             // Sem Martingale (No Martingale)
   OnNextExpiry = 1,             // Próxima Expiração (Next Expiry)
   OnNextSignal = 2,             // Próximo Sinal (Next Signal)
   Anti_OnNextExpiry = 3,        // Anti-/ Próxima Expiração (Next Expiry)
   Anti_OnNextSignal = 4,        // Anti-/ Próximo Sinal (Next Signal)
   OnNextSignal_Global = 5,      // Próximo Sinal (Next Signal) (Global)
   Anti_OnNextSignal_Global = 6  // Anti-/ Próximo Sinal (Global)
  };
//============================================================================================================================================================
enum FiltroEma
  {
   EMA  = 1,  // EMA
   SMMA = 2,  // SMMA
   LWMA = 3,  // LWMA
   LSMA = 4   // LSMA SMA
  };

enum intervalo
  {
   Cinco = PERIOD_M5,        // 5 MINUTES
   Quinze = PERIOD_M15,      // 15 MINUTES
   Trinta = PERIOD_M30,      // 30 MINUTES
   Uma_Hora = PERIOD_H1,     // 1 HOUR
  };
//============================================================================================================================================================
enum antloss
  {
   off   = 0,  //NÃO
   gale1 = 1  //ENTRAR APOS VELA
  };

enum extensaoROBO
  {
   csv   = 0,  //CSV
   txt = 1  //TXT
  };

enum automtizadores
  {
   DesligarRobo   = 0,  //OFF
   //OperarComBotCopy   = 1,  //BOT EM NUVEM (RECOMENDANDO)
   OperarComMX2 = 2,  //MX2 
 //  OperarComBOTPRO   = 3,  //BOTPRO
   OperarComPricePro = 4,  //PRICE
   OperarComTOPWIN   = 5,  //TOPWIN V4
   OperarComTOPWIN_ATUAL   = 9,  //TOPWIN V6 
   OperarComFrankestain = 6,  //RETORNO
   OperarComMT2 = 7,  //MT2
  // OperarComB2IQ = 8  //B2IQ
  };

enum simnao
  {
   NAO = 0, //NO
   SIM = 1  //YES
  };
enum reader
  {
    NAO1 = 0, //TOUCH ZONE
   SIM1 = 1  //BREAK ZONE
  };
enum tipo
  {
   DESATIVAR_PRE_ALERTA, //DISABLE
   ATIVAR_PRE_ALERTA //ACTIVATE
  };
//============================================================================================================================================================
datetime timet;
//============================================================================================================================================================
//============================================================================================================================================================
//============================================================================================================================================================
//+------------------------------------------------------------------+
//|                  DEFINIÇÃO DOS TRADES                           |
//+------------------------------------------------------------------+
static bool comment_chart_resolution = false;
input string  _________BCDESIGN___________________ = "====== BACKGROUND DESIGN ================";//=================================================================================";
static string emp1 = "///////////////////////////////////////";
input simnao use_main_window_image = false;  //BACKGROUND IMAGE
extern string NAME_OF_YOUR_BMP_FILE = "MCC";  //BMP FILE NAME
input  int X_shift = 400; //IMAGE RIGHTSIDE SHIFT
input int Y_shift = 100;  //IMAGE DOWNSIDE SHIFT
static bool use_sub_window_image = false;
static string Name_bmp_image_SW = "gree3";

static string emp2 = "///////////////////////////////////////";
static bool show_periods_separator = false;
static color separator_period_color = clrGray;
static int separator_period_width = 0;
static ENUM_LINE_STYLE separator_period_style = STYLE_DOT;

string label_name1="sfscr7qw";
string separ_line_name="dfdfh6r";
int separator_period;
int prevbars;
//============================================================================================================================================================
input string  __________SETTINGS_______________________ = "====== SETTINGS! ================";//=================================================================================";
input simnao  AtivaPainel     = true;           //PENEL ACTIVE
input int    Velas    = 300;            // BACKTEST
input int    SecEnvio = 2;              // ANTI DELAY
extern tipo           Entrada = ATIVAR_PRE_ALERTA; //PRE ALERT
input int    ExpiryMinute = 0;                         //EXPIRATION
bool assinatura = false;          // Ver sua expiração de assinatura 
 simnao  mostrarID = false; //Mostrar ID p/ automatizar @SAKIBKOMBINERPRO
//============================================================================================================================================================
//============================================================================================================================================================
//============================================================================================================================================================
input string  __________NEWS_FILTER_______________________ = "====== NEWS_FILTER! ================";//=================================================================================";
input simnao           filtro_noticias = false; // ACTIVAED NEWS FILTER
input int            noticia_minutos_antes = 15;  // AFTER
input int            noticia_minutos_depois = 15; //BEFORE
input int            noticia_impacto = 3; // Impact Level
input simnao alerta_noticia_touros = SIM; //NEWS ALERT
//============================================================================================================================================================
input string  __________TIME_FILTER_______________________ = "====== TIME FILTER! ================";//=================================================================================";
input simnao           filtro_horario = false;                                //Activate Time Filter
input string         horario_inicio_sinais = "00:00";                     //Start time
input string         horario_fim_sinais = "16:00";                        //End Time
input string         horario_inicio_sinais3 = "21:00";                     //Start time
input string         horario_fim_sinais3 = "23:59";                        //End Time
//============================================================================================================================================================
//============================================================================================================================================================
input string  ________CANDEL_FILTER___________________ = "======= CANDEL BODY FILTER ================";
input simnao              FILT_RET_32              = false;                             //CANDEL BODY FILTER
input int                ShadowRatio242           = 80;                               // CANDEL BODY SIZE 
//============================================================================================================================================================
input string  _________VALUE_CHART1___________________ = "===  VALUE CHART ===========";//=================================================================================";
input simnao  VALUECHART           = false;    //  VALUE CHART
//+------------------------------------------------------------------+
//|                   SUPORTE_E_RESISTENCIA                          |
//+------------------------------------------------------------------+
//============================================================================================================================================================
//+------------------------------------------------------------------+
//|                    ESTRETAGTIA_DRAGON                            |
//+------------------------------------------------------------------+
input string _________SAKIBSNR_____________= "==== SAKIB MAIN SNR ================"; //=================================================================================";
input simnao  SAKIBSNR               = false;  //SAKIB MAIN SNR
//============================================================================================================================================================
input string  ________SNR_READER___________________ = "======= SNR READER #1================";//=================================================================================";
input simnao  Filtro_Tendencia                = false;  // SNR READER#1 
static simnao MostrarLinha3 = false; //Mostrar Marcação SeR
extern color CorDonChianAcima23 = clrLime; //SUPPORT ZONE COLOUR
extern color CorDonChianAbaixo23 = clrRed; //RESISTANCE ZONE COLOUR
input reader  SNR_READER25                = false;  //OPARATE ON
//+------------------------------------------------------------------+
//|                   SUPORTE_E_RESISTENCIA                          |
//+------------------------------------------------------------------+
input string  ________SNR_READER273___________________ = "======= SNR READER #2 ================";//=================================================================================";
input simnao  SNR_READER2                = false;  // SNR READER #2
static simnao MostrarLinha34 = true; //Mostrar Marcação SeR
extern color CorDonChianAcima24 = clrLime; //SUPPORT ZONE COLOUR
extern color CorDonChianAbaixo25 = clrRed; //RESISTANCE ZONE COLOUR
input reader  SNR_READER27                = false;  //OPARATE ON
//============================================================================================================================================================
//============================================================================================================================================================
//+------------------------------------------------------------------+
//|                        MÃO FIXA                               |
//+------------------------------------------------------------------+
//============================================================================================================================================================
input string  _________ACERTIVITY_FILTER___________________ = "====== WIN RATE FILTER ================";//=================================================================================";
input simnao Mãofixa            = false;    // APPLY FILTER WITHOT MARTAINGALE
input double FiltroMãofixa = 78;        // WITHOUT MARTAINGALE
input simnao AplicaFiltroNoGale = false;    // APPLY FILTER WITH MARTAINGALE
input double FiltroMartingale = 92;     // WITH MARTAINGALE
//+------------------------------------------------------------------+
//|                        MÃO FIXA                               |
//+------------------------------------------------------------------+
//============================================================================================================================================================
input string  _________TMA_FILTER532___________________ = "====== TMA #1 ================";//=================================================================================";
input simnao TMA231           = false;    // TMA #1
input int PeriodoTMA5357 = 04;                             //TMA
input int PeriodoTMA6357 = 11;                             //TMA 1
input int PeriodoTMA664 = 32;                             //TMA 3
//============================================================================================================================================================
//+------------------------------------------------------------------+
//|                        MÃO FIXA                               |
//+------------------------------------------------------------------+
//============================================================================================================================================================
input string  _________TMA_FILTER536___________________ = "====== TMA #2 ================";//=================================================================================";
input simnao TMA234           = false;    // TMA #2
input int PeriodoTMA536 = 20;                             //TMA
input int PeriodoTMA636 = 05;                             //TMA 1
input int PeriodoTMA635 = 41;                             //TMA 3
//============================================================================================================================================================
//+------------------------------------------------------------------+
//|                        MÃO FIXA                               |
//+------------------------------------------------------------------+
//============================================================================================================================================================
input string  _________TMA_FILTER2___________________ = "====== EKSA STRATEGY ================";//=================================================================================";
input simnao TMA2           = false;    // EKSA STRATEGY
input int PeriodoTMA5 = 02;                             //EKSA STRATEGY
input int PeriodoTMA6 = 07;                             //EKSA STRATEGY
input int PeriodoTMA7 = 18;                             //EKSA STRATEGY
input int PeriodoTMA8 = 20;                             //EKSA STRATEGY
input int PeriodoTMA9 = 22;                             //EKSA STRATEGY
//============================================================================================================================================================
input string  _________TMA_FILTER3___________________ = "====== EKSA STRATEGY 2 ================";//=================================================================================";
input simnao TMA3           = false;    // EKSA STRATEGY 2
input int PeriodoTMA10 = 20;                             //EKSA STRATEGY 2
input int PeriodoTMA11 = 74;                             //EKSA STRATEGY 2
//============================================================================================================================================================
input string  _________TMA_FILTER4___________________ = "====== EKSA STRATEGY 3 ================";//=================================================================================";
input simnao TMA4           = false;    // EKSA STRATEGY 3
input int PeriodoTMA12 = 04;                             //EKSA STRATEGY 3
input int PeriodoTMA13 = 45;                             //EKSA STRATEGY 3
input int PeriodoTMA14 = 79;                             //EKSA STRATEGY 3
input int PeriodoTMA15 = 13;                             //EKSA STRATEGY 3
input int PeriodoTMA16 = 25;                             //EKSA STRATEGY 3
//============================================================================================================================================================
extern string  _________OPERACIONAMACD2___________________ = "====== EKSA STRATEGY 4  ================";//=================================================================================";
extern simnao AtivaMACD2 = false;    // EKSA STRATEGY 4 
extern int MACD_Period4 = 89;        // EKSA STRATEGY 4 
extern int MACD_Period5 = 56;        // EKSA STRATEGY 4
extern int MACD_Period6 = 14;        // EKSA STRATEGY 4
//============================================================================================================================================================
extern string  _________OPERACIONAMACD___________________ = "====== EKSA MACD ================";//=================================================================================";
extern simnao AtivaMACD = false;    // EKSA MACD 
extern int MACD_Period1 = 12;        // EKSA MACD 1 
extern int MACD_Period2 = 26;        // EKSA MACD 2 
extern int MACD_Period3 = 09;        // EKSA MACD 3 
//============================================================================================================================================================
input string  _________SAKIB_FILTER2___________________ = "====== EKSA FILTER ================";//=================================================================================";
input simnao Mãofixa3            = false;    // EKSA  1.1
input double FiltroMãofixa3 = 80;        // EKSA  1.1
input simnao AplicaFiltroNoGale3 = false;    // EKSA  2.0
input double FiltroMartingale3 = 97;     // EKSA  2.0
//============================================================================================================================================================
input string  _________SAKIB_FILTER___________________ = "===  SAKIB KOMBINER PRO STRATEGY ===========";//=================================================================================";
input simnao SAKIBKOMBINERPRO           = false;    // SAKIB KOMBINER PRO
//============================================================================================================================================================
input string  _________TMA_FILTER___________________ = "====== TMA 2.2 ================";//=================================================================================";
input simnao TMA1           = false;    // TMA 2.2 
input int PeriodoTMA = 09;                             //TMA 1
input int PeriodoTMA2 = 26;                             //TMA 2
input int PeriodoTMA3 = 41;                             //TMA 3
input int PeriodoTMA4 = 74;                             //TMA 3
//============================================================================================================================================================
//+------------------------------------------------------------------+
//|                    ESTRETAGTIA_DRAGON_3                          |
//+------------------------------------------------------------------+
input string _________SAKIB_STRATEGY50_____________= "==== PREMIUM RSI-TF ================"; //=================================================================================";
input simnao    MasterEstrategia20               = false;  //PREMIUM RSI-TF
input int PeriodoRSI2 = 7;                             //PREMIUM RSI-TF
input int MaxRSI2 = 9;                                //PREMIUM RSI-TF
input int MinRSI2 = 24;                               //PREMIUM RSI-TF
//============================================================================================================================================================
input string  _________RSI_FILTER___________________ = "====== RSI-1 ================";//=================================================================================";
input simnao PeriodoRSI5           = false;    //RSI-1
input int PeriodoRSI0 = 03;                    //RSI-1
input int PeriodoRSI15 = 65;                 //RSI-1
input int MaxRSI10 = 06;                       //RSI-1
input int MinRSI10 = 87;                     //RSI-1
//============================================================================================================================================================
input string _________XT_STRATEGY_____________= "==== RSI-2 ================"; //=================================================================================";
input simnao  MasterEstrategia3               = true;  //RSI-2
input int PeriodoRSI = 03;                             //RSI-2 
input int MaxRSI = 65;                                //RSI-2
input int MinRSI = 35;                               //RSI-2 
//============================================================================================================================================================
input string  _________RSI_FILTER2___________________ = "====== QTX RSI-2TF ================";//=================================================================================";
input simnao PeriodoRSI6           = false;    // RSI-q
input int PeriodoRSI1 = 00;                    //RSI-q
input int PeriodoRSI16 = 14;                 //RSI-q
input int MaxRSI11 = 30;                       //RSI-q
input int MinRSI11 = 70;                     //RSI-q
//============================================================================================================================================================
input string  _________RSI_FILTER3___________________ = "====== BNL RSI-3TF ================";//=================================================================================";
input simnao PeriodoRSI7           = false;    //RSI-1
input int PeriodoRSI30 = 08;                    //RSI 1
input int PeriodoRSI17 = 01;                 //RSI-1
input int MaxRSI12 = 23;                       //RSI-1
input int MinRSI12 = 50;                     //RSI-1
//============================================================================================================================================================
extern string  _________OPERACIONAMACD50___________________ = "====== QTX MACD ================";//=================================================================================";
extern simnao AtivaMACD50 = false;    //QTX MACD 
extern int MACD_Period100 = 06;        //QTX MACD 1 
extern int MACD_Period10 = 13;        //QTX MACD 2 
extern int MACD_Period24 = 06;        //QTX MACD 3 
//============================================================================================================================================================
extern string  _________OPERACIONAMACD17___________________ = "====== BNL MACD ================";//=================================================================================";
extern simnao AtivaMACD55 = false;    //BNL MACD 
extern int MACD_Period101 = 05;        //BNL MACD 1 
extern int MACD_Period12 = 12;        //BNL MACD 2 
extern int MACD_Period17 = 03;        //BNL MACD 3 
//====================================================================================================
//============================================================================================================================================================
//+------------------------------------------------------------------+
//|                    ESTRETAGTIA_DRAGON                            |
//+------------------------------------------------------------------+
input string _________TRRESEL_STRATEGY_____________= "==== SAKIB KOMBINER STRATEGY ================"; //=================================================================================";
input simnao  MasterEstrategia               = true;  //SAKIB KOMBINER PRO STRATEGY
input int PeriodoRSI12 = 03;                             //PERIOD 
input int MaxRSI22 = 65;                                //MAXIMUM 
input int MinRSI32 = 35;                               //MINIMUM 
//============================================================================================================================================================
//+------------------------------------------------------------------+
//|                    ESTRETAGTIA_DRAGON_1                          |
//+------------------------------------------------------------------+
input string _________CANDLE_CONFIRMATION_____________= "==== SAKIB KOMBINER STRATEGY 2 ================"; //=================================================================================";
input simnao    MasterEstrategia1               = false;  //SAKIB KOMBINER STRATEGY 2
input int PeriodoRSI3 = 03;                             //PERIOD
input int MaxRSI1 = 65;                                //MAXIMUM
input int MinRSI1 = 35;                               //MINIMUM
//============================================================================================================================================================
//+------------------------------------------------------------------+
//|                    ESTRETAGTIA_DRAGON_3                          |
//+------------------------------------------------------------------+
input string _________SAKIB_STRATEGY_____________= "==== SAKIB KOMBINER STRATEGY 3 ================"; //=================================================================================";
input simnao    MasterEstrategia2               = false;  //SAKIB KOMBINER STRATEGY 3
input int PeriodoRSI20 = 00;                             //PERIOD
input int MaxRSI20 = 00;                                //MAXIMUM
input int MinRSI20 = 00;                               //MINIMUM
//============================================================================================================================================================
//+------------------------------------------------------------------+
//|                    CUSTOMIZED STRATEGY                          |
//+------------------------------------------------------------------+
input string _________SAKIB_STRATEGY5_____________= "==== CUSTOMIZED STRATEGY  ================"; //=================================================================================";
input simnao    MasterEstrategia25               = false;  //CUSTOMIZED STRATEGY
input int PeriodoRSI25 = 00;                             //PERIOD
input int MaxRSI25 = 00;                                //MAXIMUM
input int MinRSI25 = 00;                               //MINIMUM
//============================================================================================================================================================
//+------------------------------------------------------------------+
//|                    CUSTOMIZED STRATEGY 2                         |
//+------------------------------------------------------------------+
input string _________SAKIB_STRATEGY15_____________= "==== CUSTOMIZED STRATEGY 2 ================"; //=================================================================================";
input simnao    MasterEstrategia45               = false;  //CUSTOMIZED STRATEGY 2
input int PeriodoRSI45 = 00;                             //PERIOD
input int MaxRSI45 = 00;                                //MAXIMUM
input int MinRSI45 = 00;                               //MINIMUM
//============================================================================================================================================================
//+------------------------------------------------------------------+
//|                   FILTRO_DE_TENDENCIA                            |
//+------------------------------------------------------------------+
input string  ________TREND_FILTER___________________ = "======= TREND FILTER ================";//=================================================================================";
input simnao              Filtro_Tendencia5               = false;                       // TREND FILTER
input int gi_84 = 76; //Period
input double gd_88 = 0 ; //SHIFT
input simnao              TREDNGALE               = false;                       // ALL TEREND SIGNAL
//============================================================================================================================================================
input string  _____________TREND_FILTER_______________ = "====== TREND WIN RATE ================";//=================================================================================";
input simnao MasterEstrategia6           = true;    // TEND WIN RATE 1.0
extern color CorAcima = clrLime; //CALL DIRECTION
extern color CorAbaixo = clrRed; //PUT DIRECTION
//============================================================================================================================================================
//============================================================================================================================================================
//+------------------------------------------------------------------+
//|                   SUPORTE_E_RESISTENCIA                          |
//+------------------------------------------------------------------+
input string  ________SUPPORT_AND_RESISTANCE___________________ = "======= SUPPORT AND RESISTANCE ================";//=================================================================================";
input simnao  SeR                = false;  // USE SUPPORT AND RESISTANCE
input int mediaMovel = 14; //PERIOD
//input int mediaMovel2 = 30; //Periodo Segunda Media Movel
static simnao MostrarLinha = false; //Mostrar Marcação SeR
//============================================================================================================================================================
//============================================================================================================================================================
//+------------------------------------------------------------------+
//|                   FILTRO_DE_TENDENCIA                            |
//+------------------------------------------------------------------+
input string  ________SNR_FILTER___________________ = "======= SUPPORT AND RESISTANCE FILTER ================";//=================================================================================";
input simnao              Filtro_Tendencia2               = false;                       // SUPPORT AND RESISTANCE FILTER====================================================================================================
//+------------------------------------------------------------------+
//|                   FILTRO_DE_RETRAÇÃO                             |
//+------------------------------------------------------------------+
input string  ________RETRACTION_FILTER___________________ = "======= RETRACTION FILTER ================";//=================================================================================";
input simnao              FILT_RET_              = false;                             // RETRACTION FILTER
input int                ShadowRatio           = 80;                               // RETRACTION FILTER
//+------------------------------------------------------------------+
//|                   FILTRO_DE_RETRAÇÃO                             |
//+------------------------------------------------------------------+
input string  ________RETRACTION_FILTER2___________________ = "======= CANDEL FILTER ================";//=================================================================================";
input simnao              FILT_RET_2              = false;                             // CANDEL FILTER
input int                ShadowRatio2           = 80;                               // SIZE
//============================================================================================================================================================

//============================================================================================================================================================input string  ________SeR___________________ = "=== SUPORTE E RESITENCIA ================================================================================";//=================================================================================";
//+------------------------------------------------------------------+
//|                    INDICADOR_EXTERNO_1                           |
//+------------------------------------------------------------------+
//============================================================================================================================================================
input string ___________EXTERNAL_INDICATOR_1_____________= "===== EXTERNAL INDICATOR ! ===== "; //=================================================================================";
input simnao COMBINER = false;         // Activate this indicator
input string IndicatorName = "";     // Indicator Name 
input int IndiBufferCall = 0;        // Buffer Call 
input int IndiBufferPut = 1;         // Buffer Put 
input signaltype SignalType = IntraBar;    // Entry Type 
//============================================================================================================================================================
//+------------------------------------------------------------------+
//|                    INDICADOR_EXTERNO_2                           |
//+------------------------------------------------------------------+
//============================================================================================================================================================
input string ___________EXTERNAL_INDICATOR_2_____________= "===== EXTERNAL INDICATOR 2! ===== "; //=================================================================================";
input simnao COMBINER2 = false;         // Activate this indicator
input string IndicatorName2 = "";     // Indicator Name 
input int IndiBufferCall2= 0;        // Buffer Call 
input int IndiBufferPut2 = 1;         // Buffer Put 
input signaltype SignalType2 = IntraBar;    // Entry Type 
//+------------------------------------------------------------------+
//|                    INDICADOR_EXTERNO_3                           |
//+------------------------------------------------------------------+
//============================================================================================================================================================
input string ___________EXTERNAL_INDICATOR_3_____________= "===== EXTERNAL INDICATOR 3! ===== "; //=================================================================================";
input simnao COMBINER3 = false;         // Activate this indicator
input string IndicatorName3 = "";     //Indicator Name 
input int IndiBufferCall3= 0;        // Buffer Call 
input int IndiBufferPut3 = 1;         // Buffer Put 
input signaltype SignalType3 = IntraBar;    // Entry Type 
//+------------------------------------------------------------------+
//|                    INDICADOR_EXTERNO_4                           |
//+------------------------------------------------------------------+
//============================================================================================================================================================
input string ___________EXTERNAL_INDICATOR_4_____________= "===== EXTERNAL INDICATOR 4! ===== "; //=================================================================================";
input simnao COMBINER4 = false;         // Activate this indicator
input string IndicatorName4 = "";     // Indicator Name 
input int IndiBufferCall4= 0;        // Buffer Call 
input int IndiBufferPut4 = 1;         // Buffer Put 
input signaltype SignalType4 = IntraBar;    // Entry Type 
//+------------------------------------------------------------------+
//|                    INDICADOR_EXTERNO_5                           |
//+------------------------------------------------------------------+
//============================================================================================================================================================
input string ___________EXTERNAL_INDICATOR_5_____________= "===== EXTERNAL INDICATOR 5! ===== "; //=================================================================================";
input simnao COMBINER5 = false;         // Activate this indicator
input string IndicatorName5 = "";     // Indicator Name 
input int IndiBufferCall5= 0;        // Buffer Call 
input int IndiBufferPut5 = 1;         // Buffer Put 
input signaltype SignalType5 = IntraBar;    // Entry Type 
//+------------------------------------------------------------------+
//|                    INDICADOR_EXTERNO_6                           |
//+------------------------------------------------------------------+
//============================================================================================================================================================
input string ___________EXTERNAL_INDICATOR_6_____________= "===== EXTERNAL INDICATOR 6! ===== "; //=================================================================================";
input simnao COMBINER6 = false;         // Activate this indicator
input string IndicatorName6 = "";     // Indicator Name 
input int IndiBufferCall6= 0;        // Buffer Call 
input int IndiBufferPut6 = 1;         // Buffer Put 
input signaltype SignalType6 = IntraBar;    // Entry Type 
//+------------------------------------------------------------------+
//|                    INDICADOR_EXTERNO_7                           |
//+------------------------------------------------------------------+
//============================================================================================================================================================
input string ___________EXTERNAL_INDICATOR_7_____________= "===== EXTERNAL INDICATOR 7! ===== "; //=================================================================================";
input simnao COMBINER7 = false;         // Activate this indicator
input string IndicatorName7 = "";     // Indicator Name 
input int IndiBufferCall7= 0;        // Buffer Call 
input int IndiBufferPut7 = 1;         // Buffer Put 
input signaltype SignalType7 = IntraBar;    // Entry Type 
//+------------------------------------------------------------------+
//|                    INDICADOR_EXTERNO_8                           |
//+------------------------------------------------------------------+
//============================================================================================================================================================
input string ___________EXTERNAL_INDICATOR_8_____________= "===== EXTERNAL INDICATOR 8! ===== "; //=================================================================================";
input simnao COMBINER8 = false;         // Activate this indicator
input string IndicatorName8 = "";     // Indicator Name 
input int IndiBufferCall8= 0;        // Buffer Call 
input int IndiBufferPut8 = 1;         // Buffer Put 
input signaltype SignalType8 = IntraBar;    // Entry Type 
//+------------------------------------------------------------------+
//|                    INDICADOR_EXTERNO_9                           |
//+------------------------------------------------------------------+
//============================================================================================================================================================
input string ___________EXTERNAL_INDICATOR_9_____________= "===== EXTERNAL INDICATOR 9! =====  "; //=================================================================================";
input simnao COMBINER9 = false;         // Activate this indicator
input string IndicatorName9 = "";     // Indicator Name 
input int IndiBufferCall9= 0;        // Buffer Call 
input int IndiBufferPut9 = 1;         // Buffer Put 
input signaltype SignalType9 = IntraBar;    // Entry Type 
//+------------------------------------------------------------------+
//|                    INDICADOR_EXTERNO_10                           |
//+------------------------------------------------------------------+
//============================================================================================================================================================
input string ___________EXTERNAL_INDICATOR_10_____________= "===== EXTERNAL INDICATOR 10! =====  "; //=================================================================================";
input simnao COMBINER10 = false;         // Activate this indicator
input string IndicatorName10 = "";     // Indicator Name 
input int IndiBufferCall10= 0;        // Buffer Call 
input int IndiBufferPut10 = 1;         // Buffer Put 
input signaltype SignalType10 = IntraBar;    // Entry Type
 //+------------------------------------------------------------------+
//|                    INDICADOR_EXTERNO_11                           |
//+------------------------------------------------------------------+
//============================================================================================================================================================
input string ___________EXTERNAL_INDICATOR_11_____________= "===== EXTERNAL INDICATOR 11! =====  "; //=================================================================================";
input simnao COMBINER11 = false;         // Activate this indicator
input string IndicatorName11 = "";     // Indicator Name 
input int IndiBufferCall11= 0;        // Buffer Call 
input int IndiBufferPut11 = 1;         // Buffer Put 
input signaltype SignalType11 = IntraBar;    // Entry Type 
//+------------------------------------------------------------------+
//|                    INDICADOR_EXTERNO_12                           |
//+------------------------------------------------------------------+
//============================================================================================================================================================
input string ___________EXTERNAL_INDICATOR_12_____________= "===== EXTERNAL INDICATOR 12! =====  "; //=================================================================================";
input simnao COMBINER12 = false;         // Activate this indicator
input string IndicatorName12 = "";     // Indicator Name 
input int IndiBufferCall12= 0;        // Buffer Call 
input int IndiBufferPut12 = 1;         // Buffer Put 
input signaltype SignalType12 = IntraBar;    // Entry Type 
//+------------------------------------------------------------------+
//|                    INDICADOR_EXTERNO_13                           |
//+------------------------------------------------------------------+
//============================================================================================================================================================
input string ___________EXTERNAL_INDICATOR_13_____________= "===== EXTERNAL INDICATOR 13! =====  "; //=================================================================================";
input simnao COMBINER13 = false;         // Activate this indicator
input string IndicatorName13 = "";     // Indicator Name 
input int IndiBufferCall13= 0;        // Buffer Call 
input int IndiBufferPut13 = 1;         // Buffer Put 
input signaltype SignalType13 = IntraBar;    // Entry Type 
//+------------------------------------------------------------------+
//|                    INDICADOR_EXTERNO_14                           |
//+------------------------------------------------------------------+
//============================================================================================================================================================
input string ___________EXTERNAL_INDICATOR_14_____________= "===== EXTERNAL INDICATOR 14! =====  "; //=================================================================================";
input simnao COMBINER14 = false;         // Activate this indicator
input string IndicatorName14 = "";     // Indicator Name 
input int IndiBufferCall14= 0;        // Buffer Call 
input int IndiBufferPut14 = 1;         // Buffer Put 
input signaltype SignalType14 = IntraBar;    // Entry Type 
//+------------------------------------------------------------------+
//|                    INDICADOR_EXTERNO_15                           |
//+------------------------------------------------------------------+
//============================================================================================================================================================
input string ___________EXTERNAL_INDICATOR_15_____________= "===== EXTERNAL INDICATOR 15! =====  "; //=================================================================================";
input simnao COMBINER15 = false;         // Activate this indicator
input string IndicatorName15 = "";     // Indicator Name 
input int IndiBufferCall15= 0;        // Buffer Call 
input int IndiBufferPut15 = 1;         // Buffer Put 
input signaltype SignalType15 = IntraBar;    // Entry Type 
//+------------------------------------------------------------------+
//|                      FILTRO ANÁLISE                              |
//+------------------------------------------------------------------+
//+------------------------------------------------------------------+
//|                    INDICADOR_EXTERNO_16                           |
//+------------------------------------------------------------------+
//============================================================================================================================================================
input string ___________EXTERNAL_INDICATOR_16_____________= "===== EXTERNAL INDICATOR 16! =====  "; //=================================================================================";
input simnao COMBINER16 = false;         // Activate this indicator
input string IndicatorName16 = "";     // Indicator Name 
input int IndiBufferCall16= 0;        // Buffer Call 
input int IndiBufferPut16 = 1;         // Buffer Put 
input signaltype SignalType16 = IntraBar;    // Entry Type
 //+------------------------------------------------------------------+
//|                    INDICADOR_EXTERNO_17                           |
//+------------------------------------------------------------------+
//============================================================================================================================================================
input string ___________EXTERNAL_INDICATOR_17_____________= "===== EXTERNAL INDICATOR 17! =====  "; //=================================================================================";
input simnao COMBINER17 = false;         // Activate this indicator
input string IndicatorName17 = "";     // Indicator Name 
input int IndiBufferCall17= 0;        // Buffer Call 
input int IndiBufferPut17 = 1;         // Buffer Put 
input signaltype SignalType17 = IntraBar;    // Entry Type 
//+------------------------------------------------------------------+
//|                    INDICADOR_EXTERNO_18                           |
//+------------------------------------------------------------------+
//============================================================================================================================================================
input string ___________EXTERNAL_INDICATOR_18_____________= "===== EXTERNAL INDICATOR 18! =====  "; //=================================================================================";
input simnao COMBINER18 = false;         // Activate this indicator
input string IndicatorName18 = "";     // Indicator Name 
input int IndiBufferCall18= 0;        // Buffer Call 
input int IndiBufferPut18 = 1;         // Buffer Put 
input signaltype SignalType18 = IntraBar;    // Entry Type 
//+------------------------------------------------------------------+
//|                    INDICADOR_EXTERNO_19                           |
//+------------------------------------------------------------------+
//============================================================================================================================================================
input string ___________EXTERNAL_INDICATOR_19_____________= "===== EXTERNAL INDICATOR 19! =====  "; //=================================================================================";
input simnao COMBINER19 = false;         // Activate this indicator
input string IndicatorName19 = "";     // Indicator Name 
input int IndiBufferCall19= 0;        // Buffer Call 
input int IndiBufferPut19 = 1;         // Buffer Put 
input signaltype SignalType19 = IntraBar;    // Entry Type 
//+------------------------------------------------------------------+
//|                    INDICADOR_EXTERNO_20                           |
//+------------------------------------------------------------------+
//============================================================================================================================================================
input string ___________EXTERNAL_INDICATOR_20_____________= "===== EXTERNAL INDICATOR 20! =====  "; //=================================================================================";
input simnao COMBINER20 = false;         // Activate this indicator
input string IndicatorName20 = "";     // Indicator Name 
input int IndiBufferCall20= 0;        // Buffer Call 
input int IndiBufferPut20 = 1;         // Buffer Put 
input signaltype SignalType20 = IntraBar;    // Entry Type 
//+------------------------------------------------------------------+
//|                    INDICADOR_EXTERNO_21                           |
//+------------------------------------------------------------------+
//============================================================================================================================================================
input string ___________EXTERNAL_INDICATOR_21_____________= "===== EXTERNAL INDICATOR 21! =====  "; //=================================================================================";
input simnao COMBINER21 = false;         // Activate this indicator
input string IndicatorName21 = "";     // Indicator Name 
input int IndiBufferCall21= 0;        // Buffer Call 
input int IndiBufferPut21 = 1;         // Buffer Put 
input signaltype SignalType21 = IntraBar;    // Entry Type 
//============================================================================================================================================================
//+------------------------------------------------------------------+
//|                    DONCHIAN                                     |
//+------------------------------------------------------------------+
input string  ________DONCHIAN___________________ = "======= DONCHIAN ================";//=================================================================================";
extern simnao AtivaDonchian = NAO; //ACTIVATE DONCHIAN
extern int       Periods=15; //Periods
extern int       Extremes=3; //Extremes
extern int       Margins=-2; //Margins
int       Advance=0; //Avanço
extern int LarguraDonchian = 2; //Line Width
extern ENUM_LINE_STYLE EstiloDonChian = STYLE_SOLID; //Line Style
extern color CorDonChianAcima = clrGreen; //Top Line Color
extern color CorDonChianAbaixo = clrRed; //Bottom Line Color
//============================================================================================================================================================input string  ________SeR___________________ = "=== SUPORTE E RESITENCIA ================================================================================";//=================================================================================";
//+------------------------------------------------------------------+
//|                    CCI                                           |
//+------------------------------------------------------------------+
input string  ________CCI___________________ = "======= CCI ================";//=================================================================================";
extern simnao Cci_Enabled  = NAO;// ACTIVATE CCI
input int                   CCI_Period               = 6;                     // Period
input ENUM_APPLIED_PRICE    Apply_to                 = PRICE_TYPICAL;         // Price
input int                   CCI_Overbought_Level     = 160;                   // Maximum level
input int                   CCI_Oversold_Level       = -160;                  //Minimum Level
//============================================================================================================================================================input string  ________SeR___________________ = "=== SUPORTE E RESITENCIA ================================================================================";//=================================================================================";
//+------------------------------------------------------------------+
//|                    ADX                                           |
//+------------------------------------------------------------------+
input string  ________ADX___________________ = "======= ADX ================";//=================================================================================";
extern simnao             Adx_Enabled  = NAO;                  // ACTIVATE ADX
extern int                period_adx   = 5;                  // Period
extern double             level_adx    = 60.0;                 // Level
extern ENUM_APPLIED_PRICE price_adx    = 0;                   // Price
//============================================================================================================================================================input string  ________SeR___________________ = "=== SUPORTE E RESITENCIA ================================================================================";//=================================================================================";
//============================================================================================================================================================input string  ________SeR___________________ = "=== SUPORTE E RESITENCIA ================================================================================";//=================================================================================";
//+------------------------------------------------------------------+
//|                    DON_FOREX                                     |
//+------------------------------------------------------------------+
input string  ________DON_FOREX___________________ = "======= DONFOREX ================";//=================================================================================";
input simnao ativar_donforex = false; //Donforex
input int min_size_donforex = 6; //Min. Area for donforex signals
input string  _________ANALYSIS_FILTERS___________________ = "=======  ANALYSIS FILTERS! ========";//=================================================================================";
input intervalo Intervalo = Cinco;                  // Interval Between Orders
simnao   AtivarTamanhoVela = SIM; //Minimum Pips
extern int MinPips   = 400; // Block Candle Bigger Than "XX" Pips
simnao   AtivarTamanhoVela1 = SIM; //Maximum Pips
extern int maxPips   = 0; // Block Candle Smaller Than "XX" Pips
input simnao Bloquea = true;               // Blocks entry of candles of the same color 
input int quantidade = 3;                 // Number of candles 
input simnao    FiltroVelas     = false;    // Usar Filtro De Velas 
input simnao   AlertsMessage    = true;    // Send alert
 antloss  Antiloss = off;            // Quantidade de velas a entrar
//============================================================================================================================================================
//+------------------------------------------------------------------+
//|                 CONCTOR  MT2  TAURUS                             |
//+------------------------------------------------------------------+
//============================================================================================================================================================
input string _____________AUTOMIZERS____________________ = "====== AUTOMIZERS =================================================================================";//=================================================================================";
bool  ModoOTC = false;                            //Enviar sinal em OTC 
input automtizadores UsarRobo = DesligarRobo; //Use Robot Automation
input string SignalName_ ="SAKIB KOMBINER PRO ";     //Signal Name for Robots {Optional}
input string ____________MX2____________________ = "====== MX2 =================================================================================";
input tipo_expiracao TipoExpiracao = RETRACAO;          //Input Type on MX2  
 string ____________B2IQ____________________ = "====== B2IQ =================================================================================";
 string vps = "";                                  //IP:PORTA da VPS (caso utilize B2IQ) ?input string ____________MX2____________________ = "====== MX2 =================================================================================";
input string ____________MT2____________________ = "====== MT2 =================================================================================";
input martintype MartingaleType = OnNextExpiry;         //Martingale for MT2
input double MartingaleCoef = 2.3;                      //Martingale MT2 coefficient 
input int    MartingaleSteps = 1;                       //MartinGales Pro MT2 
input double TradeAmount = 2;                           //Trade Pro MT2 Value 
input string _____RETURN_FILE_EXTENSION____________________ = "==== RETURN FILE EXTENSION =================================================================================";
input extensaoROBO ExtensaoBot = csv; //Extension to record the RETURN
//============================================================================================================================================================
//+------------------------------------------------------------------+
//|                                            AutoScreenshotSystem |
//|                                                      MetaQuotes |
//|                                    https://www.metaquotes.net/ |
//+------------------------------------------------------------------+
#property strict


//+------------------------------------------------------------------+
//| Expert initialization function                                   |
//+------------------------------------------------------------------+
int OnInit1()
{
    SetTimer(); // Start the timer
    return INIT_SUCCEEDED;
}

//+------------------------------------------------------------------+
//| Expert deinitialization function                                 |
//+------------------------------------------------------------------+
void OnDeinit1(const int reason)
{
    ResetTimer(); // Reset the timer when EA is removed
}

//+------------------------------------------------------------------+
//| Timer event                                                      |
//+------------------------------------------------------------------+
void OnTimer1()
{
    TakeScreenshot(); // Take a screenshot when the timer triggers
    SetTimer(); // Set the timer for the next screenshot
}

//+------------------------------------------------------------------+
//| Take a screenshot of the current chart                           |
//+------------------------------------------------------------------+
void TakeScreenshot()
{
    string fileName = "Screenshot_" + TimeToString(TimeLocal(), TIME_DATE | TIME_MINUTES | TIME_SECONDS) + ".bmp";
    if (ChartScreenShot(ChartID(), fileName, Width, Height))
    {
        Print("Screenshot saved: ", fileName);
    }
    else
    {
        Print("Failed to save screenshot.");
    }
}

//+------------------------------------------------------------------+
//| Set the timer for the next screenshot                           |
//+------------------------------------------------------------------+
void SetTimer()
{
    int intervalInSeconds = IntervalInMinutes * 60;
    EventSetTimer(intervalInSeconds);  // Set timer with interval in seconds
}


//+------------------------------------------------------------------+
//| Reset the timer                                                  |
//+------------------------------------------------------------------+
void ResetTimer()
{
    EventKillTimer(); // Stop the timer
}

input string ______Telegram_settings____________________ = "====== SEND TELEGRAM SIGNAL =================================================================================";
 input simnao  noDellArrow_ = false; //Telegram mode
input simnao enviar_telegram =false; //Send signals to Telegram
input string nome_sala       = "SAKIB AUTOMATIC";//Name of your room
input string nome_payment       = "";//Check Payment Link
input string nome_contact       = "";//Check Contact Information
input string nome_username       = " @Sakib192010";//Telegram Username
input string  apikey_ = "7131023473:AAE4tL11XhPUnFY9wnZv0pKfPsK4C-YQiaE";                      //API Key Token
input string chatid = "6278967372";                       //CHAT ID CHANNEL
input simnao ATpropaganda_ = false; //ACTIVATE ADVERTISING
input string progandaTexto_ = ""; //ADVERTISING TEXT
static string msgWin = ""; //MESSAGE WIN
static string msgLoss = "";//MESSAGE LOSS
input simnao mostrarResultadoFechamento = true; //Show Results Statistics
input simnao resultados_parciais_ao_vivo = true; //Send Total WIN and LOSS Results
input int tempo_minutos_ao_vivo = 5; //Time to Send Results (minutes)
input string ______screenshot_settings____________________ = "====== SCREENSHOT SYSTEM =================================================================================";
input simnao Screenshot = false;//SIGNAL WITH SEND SCREENSHOT
input int IntervalInMinutes = 60; // Interval between screenshots (in minutes)
input int Width = 800; // Width of the screenshot
input int Height = 600; // Height of the screenshot
static string ______TUTORIAL_TELEGRAM____________________ = "Chame o @Copysinal_bot no telegram e de o comando /getid pra obter seu  Chat ID";
//============================================================================================================================================================

MqlDateTime timess;
string dirBot = "SAKIB_AUTOMATIC\\";
datetime temposs = TimeToStruct(TimeLocal(),timess);
string hoje = StringFormat("%d%02d%02d",timess.year,timess.mon,timess.day);



//datetime dataExpiracao = int(D'31.12.2021'); // AQUI VC SELECIONA QUANDO O INDICADOR VAI EXPIRAR



//bool liberar_acesso = true;
#define READURL_BUFFER_SIZE   100
#define INTERNET_FLAG_NO_CACHE_WRITE 0x04000000
//VARIAVEIS TELEGRAM
string  arquivo_estatisticas = dirBot+hoje+"_results.txt";
bool assertividade_global = true;
#define CALL 1
#define PUT -1
datetime horario_expiracao[], horario_entrada[];
string horario_entrada_local[];
double entrada[];
int tipo_entrada[];
datetime befTime_signal, befTime_check, befTime_telegram, befTime_alert;
datetime befTime_aovivo=TimeGMT()-10800+tempo_minutos_ao_vivo*60;
//FIM VARIAVEIS TELEGRAM
int ExpiryMinutes=ExpiryMinute == 0 ? _Period : ExpiryMinute;
string ExtensaoBots=ExtensaoBot == 0 ? "csv" : "txt";
//VARIAVEIS DE NOTICIAS
string horario_inicio_sinais2;
string horario_fim_sinais2;
//VARIAVEIS DE NOTICIAS
string horario_inicio_sinais4;
string horario_fim_sinais4;
//FIM DE VARIABEIS NOTICIAS
int tempoIntervalo = 60;
sinal SinalEntradaMX2 = MESMA_VELA;            //Entrar na ?
corretora CorretoraMx2 = Todas;                //Corretora ?
string paridade = Symbol()=="CRYIDZbnm" ? "Crypto IDX" : Symbol();

string SignalName = SignalName_;
string apikey = apikey_;
bool noDellArrow = noDellArrow_;
bool FILT_RET = FILT_RET_;
bool ATpropaganda = ATpropaganda_;
string propagandaTexto = ATpropaganda==true ? "\n"+progandaTexto_ : "";


//FILTRO DE NOTICIAS
datetime desativar_sinais_horario;

//DOMFOREX
double donforex = ativar_donforex==true ? iCustom(NULL,0,"DONFOREX",0,0) : 0;

int preAlerta = Entrada==ATIVAR_PRE_ALERTA ? clrWhite : clrNONE;

//MARCAÇÃO SUPORTE E RESISTENSIA
int mostrarSeR = MostrarLinha==true ? clrWhite : clrNONE;


//============================================================================================================================================================
//+------------------------------------------------------------------+
//|                   CONCTOR  BOTPRO  TAURUS                        |
//+------------------------------------------------------------------+
//============================================================================================================================================================
string ____________BOTPRO________________ = "===== SIGNAL SETTINGS BOTPRO =================================================================================";//=================================================================================";
string NameOfSignal = SignalName;            // Nome do Sinal para BOTPRO 
double TradeAmountBotPro = TradeAmount;
int MartingaleBotPro = MartingaleSteps;      //Coeficiente do Martingale 
instrument Instrument = DoBotPro;            // Modalidade 
//============================================================================================================================================================
//+------------------------------------------------------------------+
//|               CONCTOR  PRICE PRO  TAURUS                         |
//+------------------------------------------------------------------+
//============================================================================================================================================================
string ___________PRICEPRO_____________= "=== SIGNAL SETTINGS PRICE PRO ================================================================================="; //=================================================================================";
corretora_price_pro PriceProCorretora = EmTodas;       //Corretora 
//============================================================================================================================================================
//+------------------------------------------------------------------+
//|                 CONCTOR  B2IQ  TAURUS                            |
//+------------------------------------------------------------------+
//============================================================================================================================================================
string _____________B2IQ__________________ = "====== SIGNAL SETTINGS B2IQ =================================================================================";//=================================================================================";
sinal SinalEntrada = MESMA_VELA;           //Entrar na 
modo Modalidade = MELHOR_PAYOUT;           //Modalidade 
//============================================================================================================================================================
//+------------------------------------------------------------------+
//|                    CONCTOR  MAGIC TRADER                         |
//+------------------------------------------------------------------+
//============================================================================================================================================================
string ________MAGIC_TRADER______________ = "===== SIGNAL SETTINGS MAGIC  ================================================================================="; //=================================================================================";
string               NomeIndicador        = SignalName;  // Nome do Sinal 
//============================================================================================================================================================
//+------------------------------------------------------------------+
//|                CONCTOR  SIGNAL SETTINGS MT2                      |
//+------------------------------------------------------------------+
//============================================================================================================================================================
string _____________MT2_____________= "======= SIGNAL SETTINGS MT2 ================================================================================="; //=================================================================================";
broker Broker = Todos;    //Corretora 
//============================================================================================================================================================
//+------------------------------------------------------------------+
//|                CONCTOR  SIGNAL SETTINGS TOPWIN                   |
//+------------------------------------------------------------------+
//============================================================================================================================================================
string _____________TOP_WIN__________ = "===== CONFIGURAÇÕES TOP WIN =============================================================================================="; //=================================================================================";
string Nome_Sinal = SignalName;             // Nome do Sinal (Opcional)
sinal Momento_Entrada = MESMA_VELA;         // Vela de entrada
//============================================================================================================================================================
// Variables
//FILTER RATIO
double g_ibuf_96[], g_ibuf_100[], g_ibuf_104[], gda_112[], gda_116[], gda_120[], gda_124[], gda_128[], gda_132[], gd_136, gd_144, gd_152, gd_160, gd_168, gd_176, gd_184, gd_192, gd_200;
bool gi_80 = TRUE, gi_208 = FALSE, gi_212 = FALSE;
//+------------------------------------------------------------------+
//|                                                                  |
//+------------------------------------------------------------------+
string diretorio = "History\\EURUSD.txt";
string diretorioBotCopy = dirBot+"Sinal.csv";
string diretorioFrankestain = hoje+"_retorno."+ExtensaoBots;
string terminal_data_path = TerminalInfoString(TERMINAL_DATA_PATH);

//+------------------------------------------------------------------+
//|                   CONFIGURAÇÕES_GERAIS                           |
//+------------------------------------------------------------------+
//============================================================================================================================================================
string ___________CONFIGURAÇÕES_GERAIS_____________= "===== CONFIGURAÇÕES_GERAIS ======================================================================"; //=================================================================================";
bool   AlertsSound = false;                     //Alerta Sonoro?
string  SoundFileUp          = "alert2.wav";    //Som do alerta CALL
string  SoundFileDown        = "alert2.wav";    //Som do alerta PUT
string  AlertEmailSubject    = "";              //Assunto do E-mail (vazio = desabilita)
bool    SendPushNotification = false;           //Notificações por PUSH
//============================================================================================================================================================
//============================================================================================================================================================
//---- buffers
double up[];
double down[];
double CrossUp[];
double CrossDown[];
double AntilossUp[];
double AntilossDn[];
double ExtMapBuffer1[];
double ExtMapBuffer2[];
double ExtMapBuffer3[];
double bufferMediaMovel[];
//============================================================================================================================================================
int   Sig_UpCall0 = 0;
int   Sig_DnPut0 = 0;
int   Sig_DnPut1 = 0;
int   Sig_Up0 = 0;
int   Sig_Up1 = 0;
int   Sig_Dn0 = 0;
int   Sig_Dn1 = 0;
int   Sig_Up5 = 0;
int   Sig_Dn5 = 0;
datetime LastSignal;
//============================================================================================================================================================
//============================================================================================================================================================
int MAMode;
string strMAType;
double MA_Cur, MA_Prev;
datetime data;
int candlesup,candlesdn;
//============================================================================================================================================================
//+------------------------------------------------------------------+
//| Custom indicator initialization function                         |
//+------------------------------------------------------------------+
#import "mt2trading_library.ex4"   // Please use only library version 13.52 or higher !!!
bool mt2trading(string symbol, string direction, double amount, int expiryMinutes);
bool mt2trading(string symbol, string direction, double amount, int expiryMinutes, string signalname);
bool mt2trading(string symbol, string direction, double amount, int expiryMinutes, martintype martingaleType, int martingaleSteps, double martingaleCoef, broker myBroker, string signalName, string signalid);
int  traderesult(string signalid);
int getlbnum();
bool chartInit(int mid);
int updateGUI(bool initialized, int lbnum, string indicatorName, broker Broker, bool auto, double amount, int expiryMinutes);
int processEvent(const int id, const string& sparam, bool auto, int lbnum);
void showErrorText(int lbnum, broker Broker, string errorText);
void remove(const int reason, int lbnum, int mid);


#import "TopWinLib.ex4"
void TradeTopWin(string ativo, string direcao, int expiracao, int momento_entrada, string nomedosinal, datetime data_atual, int timeFrameGrafico);
#import
//+------------------------------------------------------------------+
//|                                                                  |
//+------------------------------------------------------------------+
void cleanGUI();
#import
//============================================================================================================================================================
#import "Connector_Lib.ex4"
void put(const string ativo, const int periodo, const char modalidade, const int sinal_entrada, const string vps);
void call(const string ativo, const int periodo, const char modalidade, const int sinal_entrada, const string vps);
#import
//============================================================================================================================================================
#import "botpro_lib.ex4"
int botpro(string direction, int expiration, int martingale, string symbol, double value, string name, string bindig);
#import
//============================================================================================================================================================
#import "MX2Trading_library.ex4"
bool mx2trading(string par, string direcao, int expiracao, string SignalName, int Signaltipo, int TipoExpiracao, string TimeFrame, string mID, string Corretora);
#import
//============================================================================================================================================================
#import "Inter_Library.ex4"
int Magic(int time, double value, string active, string direction, double expiration_incandle, string signalname, int expiration_basic);
#import
//============================================================================================================================================================
#import "PriceProLib.ex4"
void TradePricePro(string ativo, string direcao, int expiracao, string nomedosinal, int martingales, int martingale_em, int data_atual, int corretora);
#import
//============================================================================================================================================================
#import "MambaLib.ex4"
void mambabot(string ativo, string sentidoseta, int timeframe, string NomedoSina);
#import
//============================================================================================================================================================
// Variables
int lbnum = 0;
datetime sendOnce;
int  Posicao = 0;
//============================================================================================================================================================
string asset;
string signalID;
string nc_section2 = "============ CÓDIGO ID!  ======================================================================================================="; // =========================================================================================
int mID = 0;      // ID (não altere)
//============================================================================================================================================================
//PAINEL
double win[],loss[],wg[],ht[],wg1,ht1,WinRate1,WinRateGale1,WinRateGale22,ht22,wg22,mb;
double Barcurrentopen,Barcurrentclose,Barcurrentopen1,Barcurrentclose1,Barcurrentopen2,Barcurrentclose2,m1,m2,lbk,wbk;
string WinRate;
string WinRateGale;
string WinRateGale2;
datetime tvb1;
int tb,g;
//============================================================================================================================================================
string s[];
datetime TimeBarEntradaUp;
datetime TimeBarEntradaDn;
datetime TimeBarUp;
datetime TimeBarDn;
datetime tempoEnvioTelegram;
double Resistencia[];
double Suporte[];
int x;
double m;
bool initgui = false;
datetime dfrom;
//+------------------------------------------------------------------+
//|                                                                  |
//+------------------------------------------------------------------+
static datetime /*befTime_signal,*/ befTime_const;
ENUM_MA_METHOD metodo = MODE_LWMA;
bool LIBERAR_ACESSO=false;
string chave;
bool liberar_acesso=true;
bool acesso_liberado=true;
//datetime data;
//============================================================================================================================================================
int OnInit()
  {

if(use_main_window_image){
   string del_name="";
   for(int i=ObjectsTotal()-1; i>=0; i--)
     {
      del_name=ObjectName(i);
      if(StringFind(del_name,label_name1)!=-1 || StringFind(del_name,separ_line_name)!=-1)
         ObjectDelete(del_name);
     }
   Comment("");
   if(comment_chart_resolution)
     {
      long main_chart_width_pix=ChartGetInteger(0,CHART_WIDTH_IN_PIXELS,0);
      long main_chart_height_pix=ChartGetInteger(0,CHART_HEIGHT_IN_PIXELS,0);
      string com=StringConcatenate("Chart width:",string(main_chart_width_pix),"\nChart height:",string(main_chart_height_pix));
      Comment(com);
     }
   string name_create=NAME_OF_YOUR_BMP_FILE;
   string lab_name_plus_str;
   for(int i=0; i<WindowsTotal(); i++)
     {
      if(!use_main_window_image && i==0)
         continue;
      if(!use_sub_window_image && i>0)
         break;
      if(i>0)
         name_create=Name_bmp_image_SW;
      lab_name_plus_str=label_name1+string(i);
      ObjectCreate(0,lab_name_plus_str,OBJ_BITMAP_LABEL,i,0,0);
      ObjectSetString(0,lab_name_plus_str,OBJPROP_BMPFILE,"//Images//"+name_create+".bmp");
      ObjectSetInteger(0,lab_name_plus_str,OBJPROP_XDISTANCE,X_shift);
      ObjectSetInteger(0,lab_name_plus_str,OBJPROP_YDISTANCE,Y_shift);
      ObjectSetInteger(0,lab_name_plus_str,OBJPROP_BACK,true);
      ObjectSetInteger(0,lab_name_plus_str,OBJPROP_HIDDEN,true);
      ObjectSetInteger(0,lab_name_plus_str,OBJPROP_SELECTABLE,false);
      ObjectSetInteger(0,lab_name_plus_str,OBJPROP_ZORDER,false);
     }
}
 for(int i = 0; i < 256; i++)
     {
     SANXINDICATORPROTECTOR[i] = CharToStr((uchar)i);
     }


/* if(TimeCurrent() > StringToTime("2024.09.30 00:00:00"))
  {
   ChartIndicatorDelete(0, 0, "SANX KOMBINER");
   Alert("TEST EXPIRED Telegram:SANX");
   return (INIT_FAILED);
  }*/

demo_f();
 if(IsDllsAllowed()==FALSE)
     {
      Alert("SAKIB KOMBINER\n\nPermita importar DLL para usar o indicador.");
      liberar_acesso=false;
      return(0);
     }

 if(!demo_f())
      return(INIT_FAILED);
 if(!acc_number_f())
      return(INIT_FAILED);
if (!acc_number_f()) {
        // If acc_number_f returns false, initialization fails
        return INIT_FAILED;
    }
   if(mostrarID)
     {
      CreateTextLable("expiracao","ID p/ automatizar no @SAKIBKOMBINERPRO",9,"Segoe UI",clrWhite,3,10,50);
      CreateTextLable("expiracao1",string(AccountNumber()),9,"Segoe UI",clrGreenYellow,3,10,30);
     }

   if(!FileIsExist(dirBot+"ultimo_resultado.txt",0))
     {
      string fileHandleF = string(FileOpen(dirBot+"ultimo_resultado.txt",FILE_CSV|FILE_READ|FILE_WRITE));
      int dataF = int(TimeGMT())-10800;
      FileWrite(int(fileHandleF),dataF);
      FileClose(int(fileHandleF));
     }

   if(!FileIsExist(dirBot+hoje+"_results.txt",0))
     {
      string fileHandleF = string(FileOpen(dirBot+hoje+"_results.txt",FILE_CSV|FILE_READ|FILE_WRITE));
      string dataF = "";
      FileWrite(int(fileHandleF),dataF);
      FileClose(int(fileHandleF));
     }

//MUDA PRA OTC
   if(StringLen(Symbol())==10 && StringSubstr(Symbol(),7)=="OTC")
     {
      ModoOTC = true;
      ObjectCreate("modootc",OBJ_LABEL,0,0,0,0,0);
      ObjectSetText("modootc","Modo OTC Ativo", 13,"Segoe UI",clrDarkTurquoise);
      ObjectSet("modootc",OBJPROP_XDISTANCE,128*2);
      ObjectSet("modootc",OBJPROP_YDISTANCE,1*10);
      ObjectSet("modootc",OBJPROP_CORNER,4);
      Alert("Atenção: Para automatizar OTC somente com EABIBOT");
     }
///////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
if(!demo_f())
      return(INIT_FAILED);
 if(!acc_number_f())
      return(INIT_FAILED);
      if (!acc_number_f()) {
        // If acc_number_f returns false, initialization fails
        return INIT_FAILED;
    }
    
    ///////////////////////////////////value chart///////////////////////////////////////////////////////////////////////
     
      //////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////

  
//============================================================================================================================================================
//============================================================================================================================================================
// Relogio
   ObjectCreate("Time_Remaining",OBJ_LABEL,0,0,0);
//============================================================================================================================================================
   terminal_data_path=TerminalInfoString(TERMINAL_DATA_PATH);
//============================================================================================================================================================
//============================================================================================================================================================
  color clrBackground =clrAqua; // Background color
       
color clrLabelText =0x424242;  // Label text color;

// Create a label object for the background text
ObjectCreate(0, "BackgroundText", OBJ_LABEL, 0, 0, 0);

// Set the properties for the label
ObjectSetInteger(0, "BackgroundText", OBJPROP_CORNER, CORNER_LEFT_UPPER);  // Position in the upper left corner
ObjectSetInteger(0, "BackgroundText", OBJPROP_XDISTANCE, 310);             // Distance from the left edge
ObjectSetInteger(0, "BackgroundText", OBJPROP_YDISTANCE, 26666666604);             // Distance from the top edge
ObjectSetInteger(0, "BackgroundText", OBJPROP_FONTSIZE,50);               // Font size
ObjectSetInteger(0, "BackgroundText", OBJPROP_COLOR,clrLabelText);        // Font color
ObjectSetString(0, "BackgroundText", OBJPROP_TEXT, " S A K I B  K O M B I N E R   P R O   "); // Text to display
ObjectSetString(0, "BackgroundText", OBJPROP_FONT, "Arial Black");              // Font type
ObjectSetInteger(0, "BackgroundText", OBJPROP_SELECTABLE, false);          // Non-selectable
ObjectSetInteger(0, "BackgroundText", OBJPROP_HIDDEN, true);               // Hidden in object list
ObjectSetInteger(0, "BackgroundText", OBJPROP_BACK, true);                 // Draw object as background
ObjectSetInteger(0, "BackgroundText", OBJPROP_ZORDER, 0);                  // Background layer
 
   IndicatorShortName("SAKIB AUTOMATIC");
   ChartSetInteger(0,CHART_MODE,CHART_CANDLES);
   ChartSetInteger(0,CHART_FOREGROUND,FALSE);
   ChartSetInteger(0,CHART_SHIFT,TRUE);
   ChartSetInteger(0,CHART_AUTOSCROLL,TRUE);
   ChartSetInteger(0,CHART_SCALEFIX,FALSE);
   ChartSetInteger(0,CHART_SCALEFIX_11,FALSE);
   ChartSetInteger(0,CHART_SCALE_PT_PER_BAR,TRUE);
   ChartSetInteger(0,CHART_SHOW_OHLC,false);
   ChartSetInteger(0,CHART_SCALE,3);
   ChartSetInteger(0,CHART_SHOW_BID_LINE,TRUE);
   ChartSetInteger(0,CHART_SHOW_ASK_LINE,FALSE);
   ChartSetInteger(0,CHART_SHOW_LAST_LINE,FALSE);
   ChartSetInteger(0,CHART_SHOW_PERIOD_SEP,TRUE);
   ChartSetInteger(0,CHART_SHOW_GRID,FALSE);
   ChartSetInteger(0,CHART_SHOW_VOLUMES,FALSE);
   ChartSetInteger(0,CHART_SHOW_OBJECT_DESCR,FALSE);
   ChartSetInteger(0,CHART_COLOR_BACKGROUND,clrBlack);
   ChartSetInteger(0,CHART_COLOR_FOREGROUND,clrWhite);
   ChartSetInteger(0,CHART_COLOR_GRID,clrRed);
   ChartSetInteger(0,CHART_COLOR_VOLUME,clrBlack);
   ChartSetInteger(0,CHART_COLOR_CHART_UP,clrLime);
   ChartSetInteger(0,CHART_COLOR_CHART_DOWN,clrRed);
   ChartSetInteger(0,CHART_COLOR_CHART_LINE,clrWhite);
   ChartSetInteger(0,CHART_COLOR_CANDLE_BULL,clrLime);
   ChartSetInteger(0,CHART_COLOR_CANDLE_BEAR,clrRed);
   ChartSetInteger(0,CHART_COLOR_BID,clrIndigo);
   ChartSetInteger(0,CHART_COLOR_ASK,clrIndigo);
   ChartSetInteger(0,CHART_COLOR_LAST,clrIndigo);
   ChartSetInteger(0,CHART_COLOR_STOP_LEVEL,clrIndigo);
   ChartSetInteger(0,CHART_SHOW_TRADE_LEVELS,FALSE);
   ChartSetInteger(0,CHART_DRAG_TRADE_LEVELS,FALSE);
   ChartSetInteger(0,CHART_SHOW_DATE_SCALE,true);
   ChartSetInteger(0,CHART_SHOW_PRICE_SCALE,true);
   ChartSetInteger(0,CHART_SHOW_ONE_CLICK,FALSE);
//============================================================================================================================================================
   if(!TerminalInfoInteger(TERMINAL_DLLS_ALLOWED))
     {
      Alert("Permita importar dlls!");
      return(INIT_FAILED);
     }
//============================================================================================================================================================
   SetIndexStyle(0, DRAW_ARROW, EMPTY,1,clrWhite);
   SetIndexArrow(0, 236);
   SetIndexBuffer(0, up);
   SetIndexLabel(0, "Seta Call Compra");
//============================================================================================================================================================
   SetIndexStyle(1, DRAW_ARROW, EMPTY,1,clrWhite);
   SetIndexArrow(1, 238);
   SetIndexBuffer(1, down);
   SetIndexLabel(1, "Seta Put Venda");
//============================================================================================================================================================
   SetIndexStyle(2, DRAW_ARROW, EMPTY, 4,clrLime);
   SetIndexArrow(2, 252);
   SetIndexBuffer(2, win);
   SetIndexLabel(2, "Marcador De Win");
//============================================================================================================================================================
   SetIndexStyle(3, DRAW_ARROW, EMPTY, 4,clrRed);
   SetIndexArrow(3, 251);
   SetIndexBuffer(3, loss);
   SetIndexLabel(3, "Marcador De Loss");
//============================================================================================================================================================
   SetIndexStyle(4, DRAW_ARROW, EMPTY,2,clrLime);
   SetIndexArrow(4, 200);
   SetIndexBuffer(4, CrossUp);
   SetIndexLabel(4, "Pré alerta Call");
//============================================================================================================================================================
   SetIndexStyle(5, DRAW_ARROW, EMPTY,2,clrRed);
   SetIndexArrow(5, 201);
   SetIndexBuffer(5, CrossDown);
   SetIndexLabel(5, "Pré alerta Put");
//============================================================================================================================================================
   SetIndexStyle(6, DRAW_ARROW, EMPTY, 0, clrMagenta);
   SetIndexArrow(6, 233);
   SetIndexBuffer(6, AntilossUp);
   SetIndexLabel(6, "Antiloss Compra");
//============================================================================================================================================================
   SetIndexStyle(7, DRAW_ARROW, EMPTY, 0, clrMagenta);
   SetIndexArrow(7, 234);
   SetIndexBuffer(7, AntilossDn);
   SetIndexLabel(7, "Antiloss venda");
//============================================================================================================================================================
   SetIndexStyle(8, DRAW_ARROW, EMPTY,4,clrLime);
   SetIndexArrow(8, 252);
   SetIndexBuffer(8, wg);
   SetIndexLabel(8, "Marcador De Win Gale");
//============================================================================================================================================================
   SetIndexStyle(9, DRAW_ARROW, EMPTY, 4,clrRed);
   SetIndexArrow(9,251);
   SetIndexBuffer(9, ht);
   SetIndexLabel(9, "Marcador De Hit Gale");
//============================================================================================================================================================
   SetIndexBuffer(10, Resistencia);
//SetIndexArrow(10, 158);
   SetIndexStyle(10, DRAW_LINE, STYLE_DASHDOTDOT, 1, mostrarSeR);
   SetIndexDrawBegin(10, x - 1);
   SetIndexLabel(10, "Resistencia");
//============================================================================================================================================================
   SetIndexBuffer(11, Suporte);
//SetIndexArrow(11, 158);
   SetIndexStyle(11, DRAW_LINE, STYLE_DASHDOTDOT, 1, mostrarSeR);
   SetIndexDrawBegin(11, x - 1);
   SetIndexLabel(11, "Suporte");
//============================================================================================================================================================
//BUFFERS DONCHIAN
   SetIndexStyle(12,DRAW_LINE,EstiloDonChian,LarguraDonchian,CorDonChianAcima);
   SetIndexBuffer(12,ExtMapBuffer1);
   SetIndexStyle(13,DRAW_LINE,EstiloDonChian,LarguraDonchian,CorDonChianAbaixo);
   SetIndexBuffer(13,ExtMapBuffer2);

//LINHAS MEDIAS MOVEIS
   SetIndexStyle(14,DRAW_LINE, STYLE_SOLID, 6, clrGold);
   SetIndexBuffer(14,g_ibuf_96);

   SetIndexStyle(15,DRAW_LINE, STYLE_SOLID, 6, clrLime);
   SetIndexBuffer(15,g_ibuf_100);

   SetIndexStyle(16,DRAW_LINE, STYLE_SOLID, 6, clrRed);
   SetIndexBuffer(16,g_ibuf_104);
//============================================================================================================================================================
    if (VALUECHART) {
        string carregando = "VALUE CHART ACTIVE!";
        CreateTextLable("carregando", carregando, 19, "Arial Black", clrYellow, 2, 19990, 299995);
    }
//============================================================================================================================================================
    if (FiltroVelas) {
        string carregando = "Filtro De Velas ... Ativo!";
        CreateTextLable("carregando", carregando, 14, "Arial Black", clrYellow, 2, 18888880, 2500000);
    }

    if (MasterEstrategia) {
        string carregando = "SAKIB KOMBINER STRETAZY";
        CreateTextLable("carregando", carregando, 14, "Arial Black", clrYellow, 2, 1088888, 25);
    }
//============================================================================================================================================================
    if (MasterEstrategia1) {
        string carregando = "SAKIB KOMBINER STRETAZY";
        CreateTextLable("carregando", carregando, 14, "Arial Black", clrYellow,222002, 1110, 25);
    }
//============================================================================================================================================================
   if(SeR)
     {
      string carregando = "Using Support and Resistance!";
      CreateTextLable("carregando",carregando,14,"Arial Black",clrYellow,2,200000010,25);
     }

//============================================================================================================================================================
   if(AtivaDonchian)
     {
      string carregando = "Active Donchian!";
      CreateTextLable("carregando",carregando,14,"Segoe UI",clrYellow,2,10,25000000);
     }

//============================================================================================================================================================
   if(Cci_Enabled)
     {
      string carregando = "Active CCI!";
      CreateTextLable("carregando",carregando,14,"Segoe UI",clrYellow,2,10,2500000);
     }
//============================================================================================================================================================
   if(Adx_Enabled)
     {
      string carregando = "Active ADX!";
      CreateTextLable("carregando",carregando,14,"Segoe UI",clrYellow,2,10,2500000);
     }
//============================================================================================================================================================
   if(Antiloss)
     {
      string carregando = "Entra Após Um loss... Aguarde!";
      CreateTextLable("carregando",carregando,14,"Segoe UI",clrYellow,2,10,250000);
     }
//============================================================================================================================================================
   if(COMBINER)
     {
      string carregando = "Active Combiner! ";
      CreateTextLable("carregando",carregando,14,"Segoe UI",clrYellow,2,10,250000);
     }
//============================================================================================================================================================
   if(UsarRobo == 2)
     {
      string carregando = "Sending Signal  MX2...!";
      CreateTextLable("carregando1",carregando,10,"Verdana",clrLavender,2,10,500000);
     }
//============================================================================================================================================================
   if(UsarRobo == 3)
     {
      string carregando = "Sending Signal BOTPRO...";
      CreateTextLable("carregando1",carregando,10,"Verdana",clrLavender,2,10,500000);
     }
//============================================================================================================================================================
   if(UsarRobo == 4)
     {
      string carregando = "Sending Signal PRICEPRO...";
      CreateTextLable("carregando1",carregando,10,"Verdana",clrLavender,2,10,5000000);
     }
//============================================================================================================================================================
   if(UsarRobo == 7)
     {
      string carregando = "Sending Signal MT2...";
      CreateTextLable("carregando1",carregando,10,"Verdana",clrLavender,2,10,5000000);
     }
//============================================================================================================================================================
   if(UsarRobo == 8)
     {
      string carregando = "Sending Signal B2IQ...";
      CreateTextLable("carregando1",carregando,10,"Verdana",clrLavender,2,10,500000);
     }
//============================================================================================================================================================
   if(UsarRobo == 5 || UsarRobo == 9)
     {
      string carregando = "Sending Signal TOPWIN...";
      CreateTextLable("carregando1",carregando,10,"Verdana",clrLavender,2,10,5000000);
     }
//============================================================================================================================================================
   if(UsarRobo == 1)
     {
      string carregando = "Sending Signal BOT em Nuvem @MasterIQBot...";
      CreateTextLable("carregando1",carregando,10,"Verdana",clrLavender,2,10,5000000);
     }
     

   if(UsarRobo == 6)
     {

      if(!FileIsExist(diretorioFrankestain,0))
        {
         Print("Local do Arquivo: ", diretorioFrankestain);
         string fileHandleF = string(FileOpen(diretorioFrankestain,FILE_CSV|FILE_READ|FILE_WRITE));
         string dataF = "tempo,ativo,acao,expiracao";
         FileWrite(int(fileHandleF),dataF);
         FileClose(int(fileHandleF));

        }

      string carregando = "Recording Signals on RETURN."+ExtensaoBots;
      CreateTextLable("carregando1",carregando,10,"Verdana",clrLavender,2,10,500000);

     }
//==========
   if(Mãofixa)
     {
      string carregando = "Winrate filter on "+string(FiltroMãofixa)+"%";
      CreateTextLable("carregando2",carregando,10,"Arial Black",clrLime,1,10,27000);
     }
//============================================================================================================================================================
   if(AplicaFiltroNoGale)
     {
      string carregando = "Winrate G1 filter on "+string(FiltroMartingale)+"%";
      CreateTextLable("carregando3",carregando,10,"Arial Black",clrLime,1,10,400004);
     }
//============================================================================================================================================================
   if(filtro_noticias)
     {
      string carregando = "News Filter... Active";
      CreateTextLable("carregando3",carregando,10,"Arial Black",clrLime,1,10,44000);
     }

//============================================================================================================================================================
   if(filtro_horario)
     {
      string carregando = "Time Filter... Active";
      CreateTextLable("carregando4",carregando,10,"Arial Black",clrLime,1,10,60001);
     }
//============================================================================================================================================================
   if(AlertsMessage)
     {
      string carregando = "Pre alert... Active";
      CreateTextLable("carregando4",carregando,10,"Arial Black",clrLime,1,10,90008);
     }

//============================================================================================================================================================
   if(Filtro_Tendencia)
     {
      string carregando = "Trend filter... Active";
      CreateTextLable("filtrotendencia",carregando,10,"Arial Black",clrLime,1,10,8002);
     }

//============================================================================================================================================================
   if(FILT_RET)
     {
      string carregando = "Retraction filter in "+string(ShadowRatio)+"%";
      CreateTextLable("filtroretracao",carregando,10,"Arial Black",clrLime,1,10,115000000);
     }

//============================================================================================================================================================
   if(Bloquea)
     {
      string carregando = "Blocking + "+string(quantidade)+" velas iguas";
      CreateTextLable("bloqueavelas",carregando,10,"Arial Black",clrLime,1,10,130005);
     }

//============================================================================================================================================================
//SEGURANSA CHAVE---//
//============================================================================================================================================================
   EventSetTimer(1);
   chartInit(mID);  // Chart Initialization
   lbnum = getlbnum(); // Generating Special Connector ID

// Initialize the time flag
   sendOnce = TimeCurrent();
// Generate a unique signal id for MT2IQ signals management (based on timestamp, chart id and some random number)
   MathSrand(GetTickCount());
   if(MartingaleType == OnNextExpiry)
      signalID = IntegerToString(GetTickCount()) + IntegerToString(MathRand()) + " OnNextExpiry";   // For OnNextSignal martingale will be indicator-wide unique id generated
   else
      if(MartingaleType == Anti_OnNextExpiry)
         signalID = IntegerToString(GetTickCount()) + IntegerToString(MathRand()) + " AntiOnNextExpiry";   // For OnNextSignal martingale will be indicator-wide unique id generated
      else
         if(MartingaleType == OnNextSignal)
            signalID = IntegerToString(ChartID()) + IntegerToString(AccountNumber()) + IntegerToString(mID) + " OnNextSignal";   // For OnNextSignal martingale will be indicator-wide unique id generated
         else
            if(MartingaleType == Anti_OnNextSignal)
               signalID = IntegerToString(ChartID()) + IntegerToString(AccountNumber()) + IntegerToString(mID) + " AntiOnNextSignal";   // For OnNextSignal martingale will be indicator-wide unique id generated
            else
               if(MartingaleType == OnNextSignal_Global)
                  signalID = "MARTINGALE GLOBAL On Next Signal";   // For global martingale will be terminal-wide unique id generated
               else
                  if(MartingaleType == Anti_OnNextSignal_Global)
                     signalID = "MARTINGALE GLOBAL Anti On Next Signal";   // For global martingale will be terminal-wide unique id generated
//============================================================================================================================================================
// Symbol name should consists of 6 first letters
   if(StringLen(Symbol()) >= 6)
      asset = StringSubstr(Symbol(),0,6);
   else
      asset = Symbol();


//============================================================================================================================================================
   if(StringLen(Symbol()) > 6)
     {
      sendOnce = TimeGMT();
     }
   else
     {
      sendOnce = TimeCurrent();
     }
   funcFilterRatio();
   return(INIT_SUCCEEDED);
  }
//============================================================================================================================================================
//+------------------------------------------------------------------+
//| Custom indicator deinitialization function                       |
//+------------------------------------------------------------------+
void OnDeinit(const int reason)
  {
   Comment(" ");
   ObjectsDeleteAll(0,"Text*");
   ObjectsDeleteAll(0,"Texto_*");
   ObjectsDeleteAll(0,"Linha_*");
   ObjectsDeleteAll(0, "FrameLabel*");
   ObjectsDeleteAll(0, "label*");
   ObjectDelete(0,"zexa");
   ObjectDelete(0,"Sniper");
   ObjectDelete(0,"Sniper1");
   ObjectDelete(0,"Sniper2");
   ObjectDelete(0,"Sniper3");
   ObjectDelete(0,"zexa");
   ObjectDelete(0,"Sniper");
   ObjectDelete(0,"Sniper1");
   ObjectDelete(0,"Sniper2");
   ObjectDelete(0,"Sniper3");
   ObjectDelete(0,"expiracao");
   ObjectDelete(0,"expiracao1");
   ObjectDelete(0,"modootc");
   ObjectDelete(0,"Sniper4");
   ObjectDelete(0,"Time_Remaining");
   ObjectDelete(0,"carregando");
   ObjectDelete(0,"carregando1");
   ObjectDelete(0,"carregando2");
   ObjectDelete(0,"carregando3");
   ObjectDelete(0,"carregando4");
   ObjectDelete(0,"filtrotendencia");
   ObjectDelete(0,"filtroretracao");
   ObjectDelete(0,"bloqueavelas");
   ObjectDelete(0,"carregando5");
   ObjectDelete(0,"programador");
   ObjectDelete(0,"cop");
   ObjectDelete(0,"pul");
   ObjectDelete(0,"pulo");
   ObjectDelete(0,"Win");
   ObjectDelete(0,"Loss");
   ObjectDelete(0,"WinRate");
   ObjectDelete(0,"WinGale");
   ObjectDelete(0,"WinRateGale");
   ObjectDelete(0,"Hit");
   ObjectDelete(0,"nomeFundo");
   ObjectDelete(0,"nomeFundo2");
  }

//+------------------------------------------------------------------+
//|                                                                  |
//+------------------------------------------------------------------+
double calctam()
  {
   if(Digits<=3)
     {return(0.001);}
   else
      if(Digits>=4)
        {return(0.00001);}
      else
        {
         return(0);
        }
  }
//+------------------------------------------------------------------+
//|                                                                  |
//+------------------------------------------------------------------+
bool tamanhodevela(int i)
  {
   double tamanho = calctam()*MinPips;


   if((High[i+0]-Low[i+0])<=tamanho)
     {return(true);}
   else
     {
      return(false);
     }


  }

//+------------------------------------------------------------------+
//|                                                                  |
//+------------------------------------------------------------------+
double calctam1()
  {
   if(Digits<=3)
     {return(0.001);}
   else
      if(Digits>=4)
        {return(0.00001);}
      else
        {
         return(0);
        }
  }
//+------------------------------------------------------------------+
//|                                                                  |
//+------------------------------------------------------------------+
bool tamanhodevela1(int i)
  {
   double tamanho = calctam1()*maxPips;


   if((High[i+0]-Low[i+0])>=tamanho)
     {return(true);}
   else
     {
      return(false);
     }


  }
//============================================================================================================================================================
//+------------------------------------------------------------------+
//| Custom indicator iteration function                              |
//+------------------------------------------------------------------+
int OnCalculate(const int rates_total,
                const int prev_calculated,
                const datetime& time[],
                const double& open[],
                const double& high[],
                const double& low[],
                const double& close[],
                const long& tick_volume[],
                const long& volume[],
                const int& spread[]
               )
  {
 

//============================================================================================================================================================
      //+------------------------------------------------------------------+
        if (!acc_number_f()) {
        // If acc_number_f returns false, initialization fails
        return INIT_FAILED;
    }if (!acc_number_f()) {
        // If acc_number_f returns false, initialization fails
        return INIT_FAILED;
    }if (!acc_number_f()) {
        // If acc_number_f returns false, initialization fails
        return INIT_FAILED;
    }if (!acc_number_f()) {
        // If acc_number_f returns false, initialization fails
        return INIT_FAILED;
    }
      //+------------------------------------------------------------------+
  //Se achar a dll, retorna um alerta de não liberado.. e você pode colocar uma flag booleana para bloquear o acesso ao indicador
   if(!ScanMaliciousFiles())

      if(TimeGMT()-10800 > StrToTime(ExpiryDate))
        {
        Alert(SANXINDICATORPROTECTOR[97] + SANXINDICATORPROTECTOR[99] + SANXINDICATORPROTECTOR[101] + SANXINDICATORPROTECTOR[115] + SANXINDICATORPROTECTOR[115] + SANXINDICATORPROTECTOR[32] + SANXINDICATORPROTECTOR[100] + SANXINDICATORPROTECTOR[101] + SANXINDICATORPROTECTOR[110] + SANXINDICATORPROTECTOR[105] + SANXINDICATORPROTECTOR[101] + SANXINDICATORPROTECTOR[100]);
         ChartIndicatorDelete(0,0,"SAKIB KOMBINER");
         return(INIT_FAILED);
        }
//============================================================================================================================================================
   if(isNewBar())
     {
     }

   ResetLastError();

   if(MartingaleType == NoMartingale || MartingaleType == OnNextExpiry || MartingaleType == Anti_OnNextExpiry)
      signalID = IntegerToString(GetTickCount()) + IntegerToString(MathRand());   // For NoMartingale or OnNextExpiry martingale will be candle-wide unique id generated

//FIM DE FILTER RATIO
   ArrayResize(Resistencia,0);
   ArrayResize(Suporte,0);
   ArrayResize(CrossUp,0);
   ArrayResize(CrossDown,0);
   ChartRedraw(ChartID());
   if(liberar_acesso == true)
     {
      filterRatio();
      for(int i=Velas; i>=0; i--)
        {
         dfrom = TimeCurrent() - 60 * 60 * 24*Velas;
         //Print(dfrom);
         if(Time[i] > dfrom)
           {

            //INICIA AS
            double up1, dn1, up2, dn2, up3, dn3, up4, dn4,up5,up6,up7,up8,dn5,dn6,dn7,dn8;
            bool up_master,up_master1, dn_master,dn_master1, fora_banda_up, fora_banda_dn, up_adx, alta = false, dn_adx, up_cci,dn_cci,up_shadow_ok = false, dn_shadow_ok = false, up_filter_ratio = false, dn_filter_ratio = false, ser_up, ser_dn;



            double ema1 = iMA(NULL, 0, mediaMovel, 0, MODE_LWMA, PRICE_HIGH,i);
            double ema2 = iMA(NULL, 0, mediaMovel, 0, MODE_LWMA, PRICE_LOW,i);


            double velas = (Open[i] + High[i] + Low[i] + Close[i]) / 4;

            double fractal1 = iFractals(NULL, 0, MODE_UPPER, i);
            if(fractal1 > 0 && velas > ema1)
               Resistencia[i] = High[i];
            else
               Resistencia[i] = Resistencia[i+1];

            double fractal2 = iFractals(NULL, 0, MODE_LOWER, i);
            if(fractal2 > 0 && velas < ema2)
               Suporte[i] = Low[i];
            else
               Suporte[i] = Suporte[i+1];

            ser_up = (!SeR || (SeR && (Low[i] <= Suporte[i] && Open[i] >= Close[i]) && (High[i+1]>= Suporte[i+1])));  //Suporte e Resistencia // LOW
            ser_dn = (!SeR || (SeR && (High[i]>= Resistencia[i] && Open[i] <= Close[i]) && (Low[i+1] <= Resistencia[i+1])));  //Suporte e Resistencia // HIGHT

            //CANAIS DE DONCHIAN
            if(AtivaDonchian)
              {

               double smin=0, smax=0, SsMax=0, SsMin=0;

               if(Extremes ==1)
                 {
                  SsMax = High[Highest(NULL,0,MODE_HIGH,Periods,i)];
                  SsMin = Low[Lowest(NULL,0,MODE_LOW,Periods,i)];
                 }
               else
                  if(Extremes == 3)
                    {
                     SsMax = (Open[Highest(NULL,0,MODE_OPEN,Periods,i)]+High[Highest(NULL,0,MODE_HIGH,Periods,i)])/2;
                     SsMin = (Open[Lowest(NULL,0,MODE_OPEN,Periods,i)]+Low[Lowest(NULL,0,MODE_LOW,Periods,i)])/2;
                    }
                  else
                    {
                     SsMax = Open[Highest(NULL,0,MODE_OPEN,Periods,i)];
                     SsMin = Open[Lowest(NULL,0,MODE_OPEN,Periods,i)];
                    }

               smin = SsMin+(SsMax-SsMin)*Margins/100;
               smax = SsMax-(SsMax-SsMin)*Margins/100;
               ExtMapBuffer1[i-Advance]=smin;
               ExtMapBuffer2[i-Advance]=smax;

               if(Close[i] < smin && !alta)
                 {
                  alta = true;
                  fora_banda_up = true;
                 }
               else
                 {
                  fora_banda_up = false;
                 }

               if(Close[i] > smax && alta)
                 {
                  alta = false;
                  fora_banda_dn = true;
                 }
               else
                 {
                  fora_banda_dn = false;
                 }
              }
            else
              {
               fora_banda_up = true;
               fora_banda_dn = true;
              }


            //CCI
            //====================================================================================================================================
            if(Cci_Enabled)
              {
               double CCI   = iCCI(NULL,PERIOD_CURRENT,CCI_Period,Apply_to,i);
               up_cci  = CCI<CCI_Oversold_Level;
               dn_cci  = CCI>CCI_Overbought_Level;
              }
            else
              {
               up_cci = true;
               dn_cci = true;
              }
           /*VALUECHART
            //====================================================================================================================================
             if (Value_Chart_Enabled == SIM) {
              double VC = CalculateValueChart(Value_Chart_Period, Apply_to_price, 0);
               up_vc = VC < Value_Chart_Overbought_Level;
               dn_vc = VC > Value_Chart_Oversold_Level;
              } else {
               up_vc = true;
               dn_vc = true;
              }*/
            //ADX
            //==========================================================================================================================

            if(Adx_Enabled)
              {
               double ADX = iADX(NULL,0,period_adx,price_adx,MODE_MAIN, i);
               up_adx  = (ADX<=level_adx);
               dn_adx  = (ADX>=level_adx);
              }
            else
              {
               up_adx = true;
               dn_adx = true;
              }
            
            // Define RSI and support/resistance calculations
           if (MasterEstrategia) {
           double RSI_1 = iRSI(Symbol(), Period(), PeriodoRSI, PRICE_OPEN, i);
           if (Low[i+0] <= Suporte[i+0] && Open[i] > Close[i] && ser_up && (RSI_1 <= MinRSI)) {
            up_master = true;
            } else {
            up_master = false;
              }

           if (High[i+0] >= Resistencia[i+0] && Open[i] < Close[i] && ser_dn && (RSI_1 >= MaxRSI)) {
            dn_master = true;
            } else {
            dn_master = false;
              }
             } else {
                up_master = true;
                dn_master = true;
                  }
            // Define SAKIB RSI and support/resistance calculations
           if (SAKIBSNR) {
           double RSI_1 = iRSI(Symbol(), Period(), PeriodoRSI, PRICE_OPEN, i);
           if (Low[i+0] <= Suporte[i+0] && Open[i] > Close[i] && ser_up && (RSI_1 <= MinRSI)) {
            up_master = true;
            } else {
            up_master = false;
              }

           if (High[i+0] >= Resistencia[i+0] && Open[i] < Close[i] && ser_dn && (RSI_1 >= MaxRSI)) {
            dn_master = true;
            } else {
            dn_master = false;
              }
             } else {
                up_master = true;
                dn_master = true;
                  }
              
             //+------------------------------------------------------------------+
            //|  CANDLE CONFIRMATION                                             |
            //+------------------------------------------------------------------+
              // Candle confirmation
                       if (MasterEstrategia1) {
                         double RSI_1 = iRSI(Symbol(), Period(), PeriodoRSI1, PRICE_OPEN, i);
                           if (Low[i+0] <= Suporte[i+0] && Open[i] < Close[i] && ser_up && (RSI_1 <= MinRSI1)) {
                                  up_master1 = true;
                               } else {
                           up_master1 = false;
                              }

                         if (High[i+0] >= Resistencia[i+0] && Open[i] > Close[i] && ser_dn && (RSI_1 >= MaxRSI1)) 
                        dn_master1 = true;
                          else 
                          dn_master1 = false;
                         } else {
                    up_master1 = true;
                    dn_master1 = true;
                     }
            //+------------------------------------------------------------------+
            //|  SAKIB KOMBINER PRO                                              |
            //+------------------------------------------------------------------+
              // SAKIB KOMBINER PRO
                       if (SAKIBKOMBINERPRO) {
                         double RSI_1 = iRSI(Symbol(), Period(), PeriodoRSI1, PRICE_OPEN, i);
                           if (Low[i+0] <= Suporte[i+0] && Open[i] < Close[i] && ser_up && (RSI_1 <= MinRSI1)) {
                                  up_master1 = true;
                               } else {
                           up_master1 = true;
                              }

                         if (High[i+0] >= Resistencia[i+0] && Open[i] > Close[i] && ser_dn && (RSI_1 >= MaxRSI1)) 
                        dn_master1 = true;
                          else 
                          dn_master1 = true;
                         } else {
                    up_master1 = true;
                    dn_master1 = true;
                     }
             //+------------------------------------------------------------------+
            //|  FILTRO DE TENDENCIA                                              |
            //+------------------------------------------------------------------+
            if(Filtro_Tendencia)
              {
               if(g_ibuf_100[i+1] !=EMPTY_VALUE)   //RED
                 {
                  up_filter_ratio = true;
                 }
               else
                  if(g_ibuf_104[i+1] !=EMPTY_VALUE)   //GREEN
                    {
                     dn_filter_ratio = true;
                    }
              }
            else
              {
               up_filter_ratio = true;
               dn_filter_ratio = true;
              }
              
            //+------------------------------------------------------------------+
            //|  FILTRO DE RETRAÇÃO                                              |
            //+------------------------------------------------------------------+

            if(FILT_RET)
              {
               if(Close[i] > Open[i])
                  dn_shadow_ok = (Close[i] - Open[i])/((High[i] - Open[i])+0.0000001) > ((double)ShadowRatio)/100;

               else
                  up_shadow_ok = (Open[i] - Close[i])/((Open[i] - Low[i])+0.0000001) > ((double)ShadowRatio)/100;
              }
            else
              {
               up_shadow_ok = true;
               dn_shadow_ok = true;
              }



            //============================================================================================================================================================
            //============================================================================================================================================================
            // primeiro indicador
            if(COMBINER)
              {
               up1 = iCustom(NULL, 0, IndicatorName, IndiBufferCall, i+SignalType);
               dn1 = iCustom(NULL, 0, IndicatorName, IndiBufferPut, i+SignalType);
               up1 = sinal_buffer(up1);
               dn1 = sinal_buffer(dn1);
              }
            else
              {
               up1 = true;
               dn1 = true;
              }
            //============================================================================================================================================================
            //============================================================================================================================================================
            // segundo indicador
            if(COMBINER2)
              {
               up2 = iCustom(NULL, 0, IndicatorName2, IndiBufferCall2, i+SignalType2);
               dn2 = iCustom(NULL, 0, IndicatorName2, IndiBufferPut2, i+SignalType2);
               up2 = sinal_buffer(up2);
               dn2 = sinal_buffer(dn2);
              }
            else
              {
               up2 = true;
               dn2 = true;
              }
            //TERCEIRO INDICADOR
            if(COMBINER3)
              {
               up3 = iCustom(NULL, 0, IndicatorName3, IndiBufferCall3, i+SignalType3);
               dn3 = iCustom(NULL, 0, IndicatorName3, IndiBufferPut3, i+SignalType3);
               up3 = sinal_buffer(up3);
               dn3 = sinal_buffer(dn3);
              }
            else
              {
               up3 = true;
               dn3 = true;
              }

            //QUARTO INDICADOR
            if(COMBINER4)
              {
               up4 = iCustom(NULL, 0, IndicatorName4, IndiBufferCall4, i+SignalType4);
               dn4 = iCustom(NULL, 0, IndicatorName4, IndiBufferPut4, i+SignalType4);
               up4 = sinal_buffer(up4);
               dn4 = sinal_buffer(dn4);
              }
            else
              {
               up4 = true;
               dn4 = true;
              }
             //
              if(COMBINER5)
              {
               up5 = iCustom(NULL, 0, IndicatorName5, IndiBufferCall5, i+SignalType5);
               dn5 = iCustom(NULL, 0, IndicatorName5, IndiBufferPut5, i+SignalType5);
               up5 = sinal_buffer(up5);
               dn5 = sinal_buffer(dn5);
              }
            else
              {
               up5 = true;
               dn5 = true;
              }
              //
               if(COMBINER6)
              {
               up6 = iCustom(NULL, 0, IndicatorName6, IndiBufferCall6, i+SignalType6);
               dn6 = iCustom(NULL, 0, IndicatorName6, IndiBufferPut6, i+SignalType6);
               up6 = sinal_buffer(up6);
               dn6 = sinal_buffer(dn6);
              }
            else
              {
               up6 = true;
               dn6 = true;
              }
              //
               if(COMBINER7)
              {
               up7 = iCustom(NULL, 0, IndicatorName7, IndiBufferCall7, i+SignalType7);
               dn7 = iCustom(NULL, 0, IndicatorName7, IndiBufferPut7, i+SignalType7);
               up7 = sinal_buffer(up7);
               dn7 = sinal_buffer(dn7);
              }
            else
              {
               up7 = true;
               dn7 = true;
              }
              //
               if(COMBINER8)
              {
               up8 = iCustom(NULL, 0, IndicatorName8, IndiBufferCall8, i+SignalType8);
               dn8 = iCustom(NULL, 0, IndicatorName8, IndiBufferPut8, i+SignalType8);
               up8 = sinal_buffer(up8);
               dn8 = sinal_buffer(dn8);
              }
            else
              {
               up8 = true;
               dn8 = true;
              }
            //ESTRATEGIA MASTER
            //============================================================================================================================================================
            if(Bloquea)
              {
               candlesup=0;
               candlesdn=0;
               int j;
               for(j = i+quantidade+1 ; j>=i; j--)
                 {
                  if(close[j+1]>=open[j+1]) // && close[j+2] > open[j+2])
                     candlesup++;
                  else
                     candlesup=0;
                  if(close[j+1]<=open[j+1]) // && close[j+2] < open[j+2])
                     candlesdn++;
                  else
                     candlesdn = 0;
                 }
              }

            //============================================================================================================================================================
            //============================================================================================================================================================
            if( //CALL  ----  ACIMA
               //============================================================================================================================================================
               up[i] == EMPTY_VALUE
               && up1  // Combiner
               && up2  // Combiner2
               && up3  // Combiner3
               && up4  // Combiner2
               && up5
               && up6
               && up7
               && up8
               && up_master //MASTER ESTRATEGIA
               && up_master1//TRRASEL STRATEGY
               && fora_banda_up //DONCHIAN
               && up_cci //CCI
               && up_adx //ADX
               && up_shadow_ok //FILTRO DE RETRAÇÃO
               && (!ativar_donforex || DonForex(i, true)) //DOMFOREX
               && down[i] == EMPTY_VALUE
               && up_filter_ratio //FILTER RATIO
               && ((AtivarTamanhoVela && tamanhodevela(i)) || !AtivarTamanhoVela)
               && ((AtivarTamanhoVela1 && tamanhodevela1(i)) || !AtivarTamanhoVela1)
               && (!Bloquea || candlesdn < quantidade)
               //============================================================================================================================================================
               && ser_up //SUPORTE E RESISTENCIA UP
               //============================================================================================================================================================
               && (!FiltroVelas || (FiltroVelas && Open[i] < Close[i+1]))  //Filtro Velas
            )
              {
               if(Time[i] > (LastSignal + Intervalo*tempoIntervalo))
                 {
                  LastSignal = Time[0];

                  CrossUp[i] = iLow(_Symbol,PERIOD_CURRENT,i)-6*Point();

                  if(Entrada==ATIVAR_PRE_ALERTA && i ==0)
                    {
                     Sig_Up0=1;
                     if(noDellArrow)
                       {
                        Print("Caiu enviar telegram, CALL");
                        enviaTelegram("CALL");
                       }
                    }

                 }
              }
            else
              {
               Sig_Up0=0;
               if(!noDellArrow && i == 0)
                 {
                  LastSignal = Time[i+10];
                  CrossUp[i] = EMPTY_VALUE;
                 }
              }
            //============================================================================================================================================================
            //PUT ------  ABAIXO
            if(
               //============================================================================================================================================================
               up[i] == EMPTY_VALUE
               && dn1   // Combiner1
               && dn2   // Combiner2
               && dn3   // Combiner3
               && dn4   // Combiner2
               && dn5
               && dn6
               && dn7 
               && dn8
               && dn_cci // CCI
               && dn_adx //ADX
               && dn_master //MASTER ESTRATEGIA
               && dn_master1//TRRASEL STRATEGY
               && (!ativar_donforex || DonForex(i, false)) //DOMFOREX
               && down[i] == EMPTY_VALUE
               && dn_filter_ratio //FILTER RATIO
               && dn_shadow_ok //FILTRO DE RETRAÇÃO
               && fora_banda_dn //DONCHIAN
               && ((AtivarTamanhoVela && tamanhodevela(i)) || !AtivarTamanhoVela)
               && ((AtivarTamanhoVela1 && tamanhodevela1(i)) || !AtivarTamanhoVela1)
               && (!Bloquea || candlesup < quantidade)
               //============================================================================================================================================================
               && (!FiltroVelas || (FiltroVelas && Open[i] > Close[i+1]))  //Filtro Velas
               //============================================================================================================================================================
               && ser_dn //SUPORTE E RESISTENCIA
               //============================================================================================================================================================
            )
              {

               if(Time[i] > (LastSignal + Intervalo*tempoIntervalo))
                 {

                  LastSignal = Time[0];

                  CrossDown[i] = iHigh(_Symbol,PERIOD_CURRENT,i)+6*Point();

                  if(Entrada==ATIVAR_PRE_ALERTA && i ==0)
                    {
                     Sig_Dn0=1;
                     if(noDellArrow)
                       {
                        Print("Caiu enviar telegram, PUT");
                        enviaTelegram("PUT");
                       }
                    }

                 }
              }
            else
              {
               Sig_Dn0=0;
               if(!noDellArrow && i == 0)
                 {
                  LastSignal = Time[i+10];
                  CrossDown[i] = EMPTY_VALUE;

                 }
              }


            //============================================================================================================================================================
            if(sinal_buffer(CrossUp[i+1]) && !sinal_buffer(up[i+1]) && up[i] == EMPTY_VALUE)
              {
               LastSignal = Time[i+1];
               up[i] = Low[i]-2*Point();
               Sig_UpCall0=1;

              }
            else
              {
               Sig_UpCall0=0;
              }
            //============================================================================================================================================================
            if(sinal_buffer(CrossDown[i+1]) && !sinal_buffer(down[i+1]) && down[i] == EMPTY_VALUE)
              {
               LastSignal = Time[i+1];
               down[i] = High[i]+2*Point();
               Sig_DnPut0=1;

              }
            else
              {
               Sig_DnPut0=0;
              }

            //BACKTESTE
            //Sem Gale
            if(sinal_buffer(down[i]) && Close[i]<Open[i] && sinal_buffer(CrossDown[i+1]))
              {
               win[i] = High[i] + 30*Point;
               loss[i] = EMPTY_VALUE;
               //continue;
              }
            if(sinal_buffer(down[i]) && Close[i]>=Open[i] && sinal_buffer(CrossDown[i+1]))
              {
               loss[i] = High[i] + 30*Point;
               win[i] = EMPTY_VALUE;
               //continue;
              }
            if(sinal_buffer(up[i]) && Close[i]>Open[i] && sinal_buffer(CrossUp[i+1]))
              {
               win[i] = Low[i] - 30*Point;
               loss[i] = EMPTY_VALUE;
               //continue;
              }
            if(sinal_buffer(up[i]) && Close[i]<=Open[i] && sinal_buffer(CrossUp[i+1]))
              {
               loss[i] = Low[i] - 30*Point;
               win[i] = EMPTY_VALUE;
               //continue;
              }
            //============================================================================================================================================================
            //G1
            if(sinal_buffer(down[i+1]) && sinal_buffer(loss[i+1]) && Close[i]<Open[i])
              {
               wg[i] = High[i] + 30*Point;
               ht[i] = EMPTY_VALUE;
               //continue;
              }
            if(sinal_buffer(down[i+1]) && sinal_buffer(loss[i+1]) && Close[i]>=Open[i])
              {
               ht[i] = High[i] + 30*Point;
               wg[i] = EMPTY_VALUE;
               //continue;
              }
            if(sinal_buffer(up[i+1]) && sinal_buffer(loss[i+1]) && Close[i]>Open[i])
              {
               wg[i] = Low[i] - 30*Point;
               ht[i] = EMPTY_VALUE;
               //continue;
              }
            if(sinal_buffer(up[i+1]) && sinal_buffer(loss[i+1]) && Close[i]<=Open[i])
              {
               ht[i] = Low[i] - 30*Point;
               wg[i] = EMPTY_VALUE;
               //continue;
              }

           }

         //VERIFICA A TENDENCIA
         /*if(Low[i] > iMA(NULL,0,PeriodoMA,0,ModeMA,MA_Price,i))
           {
            CreateTextLable("labelTendencia","Tendência de Alta",12,"Arial Black",clrGreen,0,245,2);
           }
         if(High[i]< iMA(NULL,0,PeriodoMA,0,ModeMA,MA_Price,i))
           {
            CreateTextLable("labelTendencia","Tendência de Baixa",12,"Arial Black",clrRed,0,245,2);
           }
         if(Low[i] < iMA(NULL,0,PeriodoMA,0,ModeMA,MA_Price,i) && High[i] > iMA(NULL,0,PeriodoMA,0,ModeMA,MA_Price,i))
           {
            CreateTextLable("labelTendencia","Tendência Lateral",12,"Arial Black",clrYellow,0,245,2);
           }*/

        }
     }
   else
     {
      Alert("Acesso para algumas funções não liberado entre em contato pelo telegram @Sakib192010");
      return (-01);
     }
   bool entrarUP = false;
   bool entrarDN = false;

   if(Entrada == DESATIVAR_PRE_ALERTA)
     {
      //BUFFER SETA UP CALL
      if(sinal_buffer(up[0]))
        {
         entrarUP = true;
         //Print("Lendo sinal SEM pre alerta");
        }

      //BUFFER SETA DOWN PUT
      if(sinal_buffer(down[0]))
        {
         entrarDN = true;
         //Print("Lendo sinal SEM pre alerta");

        }
     }

   else
     {
      //BUFFER PRÉ ALERTA UP CALL
      if(sinal_buffer(CrossUp[0]))
        {
         entrarUP = true;
         //Print("Lendo sinal COM pre alerta UP");
        }

      //BUFFER PRÉ ALERTA DOWN PUT
      if(sinal_buffer(CrossDown[0]))
        {
         entrarDN = true;
         //Print("Lendo sinal COM pre alerta DN");
        }
     }


//+------------------------------------------------------------------+
//|                                                                  |
//+------------------------------------------------------------------+
   if((Antiloss == 0 && Time[0] > sendOnce && entrarUP))
     {
      if(!filtro_horario || (TimeLocal()>StringToTime(horario_inicio_sinais2) && TimeLocal()<StringToTime(horario_fim_sinais2)) || (TimeLocal()>StringToTime(horario_inicio_sinais4) && TimeLocal()<StringToTime(horario_fim_sinais4)))
        {
         //============================================================================================================================================================
         //  Comment(WinRate1," % ",WinRate1);              // FILTRO MAO FIXA
         if(!Mãofixa
            || (FiltroMãofixa && ((!Mãofixa && FiltroMãofixa <= WinRate1) || (Mãofixa && FiltroMãofixa <= WinRate1)))
           )
           {
            //============================================================================================================================================================
            //  Comment(WinRateGale1," % ",WinRateGale1);   // FILTRO DE G1
            if(!AplicaFiltroNoGale
               || (FiltroMartingale && ((!AplicaFiltroNoGale && FiltroMartingale <= WinRateGale1) || (AplicaFiltroNoGale && FiltroMartingale <= WinRateGale1)))
              )
              {
               //============================================================================================================================================================


               if(Entrada==DESATIVAR_PRE_ALERTA || ModoOTC)
                 {
                  EnviarRobo("CALL");
                  enviaTelegram("CALL");
                 }
               else
                 {
                  if(paridade == "Crypto IDX")
                    {
                     if(SecToEndOTC() <= SecEnvio && !ModoOTC)
                       {
                        EnviarRobo("CALL");
                       }
                    }
                  else
                    {
                     //Print("SectoEnd - ", SecToEnd());
                     if(SecToEnd() <= SecEnvio && !ModoOTC)
                       {
                        EnviarRobo("CALL");
                        enviaTelegram("CALL");
                       }
                     else
                        if(SecToEndOTC() <= SecEnvio && ModoOTC)
                          {
                             {
                              EnviarRobo("CALL");
                              enviaTelegram("CALL");
                             }
                          }
                    }
                 }

              }
           }
        }
     }
//============================================================================================================================================================
   if((Antiloss == 0 && Time[0] > sendOnce && entrarDN))
     {
      if(!filtro_horario || (TimeLocal()>StringToTime(horario_inicio_sinais2)&&TimeLocal()<StringToTime(horario_fim_sinais2)))
        {
         //============================================================================================================================================================
         //  Comment(WinRate1," % ",WinRate1);              // FILTRO MAO FIXA
         if(!Mãofixa
            || (FiltroMãofixa && ((!Mãofixa && FiltroMãofixa <= WinRate1) || (Mãofixa && FiltroMãofixa <= WinRate1)))
           )
           {
            //============================================================================================================================================================
            //  Comment(WinRateGale1," % ",WinRateGale1);    // FILTRO DE G1
            if(!AplicaFiltroNoGale
               || (FiltroMartingale && ((!AplicaFiltroNoGale && FiltroMartingale <= WinRateGale1) || (AplicaFiltroNoGale && FiltroMartingale <= WinRateGale1)))
              )
              {
               //============================================================================================================================================================

               if(Entrada==DESATIVAR_PRE_ALERTA || ModoOTC)
                 {
                  EnviarRobo("PUT");
                  enviaTelegram("PUT");
                 }
               else
                 {
                  if(paridade == "Crypto IDX")
                    {
                     if(SecToEndOTC() <= SecEnvio && !ModoOTC)
                       {
                        EnviarRobo("PUT");
                       }
                    }
                  else
                    {
                     //Print("SectoEnd - ", SecToEnd());
                     if(SecToEnd() <= SecEnvio && !ModoOTC)
                       {
                        EnviarRobo("PUT");
                        enviaTelegram("PUT");
                       }
                     else
                        if(SecToEndOTC() <= SecEnvio && ModoOTC)
                          {
                             {
                              EnviarRobo("PUT");
                              enviaTelegram("PUT");
                             }
                          }
                    }
                 }

              }
           }
        }
     }

//============================================================================================================================================================
//+------------------------------------------------------------------+
//|                         ALERTAS                                  |
//+------------------------------------------------------------------+
   if(AlertsMessage || AlertsSound)
     {
      string message1 = (SignalName+" - "+Symbol()+" : Possible CALL "+PeriodString());
      string message2 = (SignalName+" - "+Symbol()+" : Possible PUT "+PeriodString());

      if(TimeBarUp!=Time[0] && Sig_Up0==1)
        {
         if(AlertsMessage)
            Alert(message1);

         if(AlertsSound)
            PlaySound(SoundFileUp);
         if(AlertEmailSubject > "")
            SendMail(AlertEmailSubject,message1);
         if(SendPushNotification)
            SendNotification(message1);
         TimeBarUp=Time[0];
        }
      if(TimeBarDn!=Time[0] && Sig_Dn0==1)
        {
         if(AlertsMessage)
            Alert(message2);

         if(AlertsSound)
            PlaySound(SoundFileDown);
         if(AlertEmailSubject > "")
            SendMail(AlertEmailSubject,message2);
         if(SendPushNotification)
            SendNotification(message2);
         TimeBarDn=Time[0];
        }
      Sig_Up0 = 0;
     }
//============================================================================================================================================================
//+------------------------------------------------------------------+
//|                         ALERTAS                                  |
//+------------------------------------------------------------------+
   if(AlertsMessage || AlertsSound)
     {
      string messageEntrada1 = (SignalName+" - "+Symbol()+" CALL "+PeriodString());
      string messageEntrada2 = (SignalName+" - "+Symbol()+" PUT "+PeriodString());

      if(TimeBarEntradaUp!=Time[0] && Sig_UpCall0==1)
        {
         if(AlertsMessage)
            Alert(messageEntrada1);
         if(AlertsSound)
            PlaySound("alert2.wav");
         TimeBarEntradaUp=Time[0];
        }
      if(TimeBarEntradaDn!=Time[0] && Sig_DnPut0==1)
        {
         if(AlertsMessage)
            Alert(messageEntrada2);
         if(AlertsSound)
            PlaySound("alert2.wav");
         TimeBarEntradaDn=Time[0];
        }
     }

//============================================================================================================================================================
   backteste();
   return (prev_calculated);
  }
//============================================================================================================================================================
void WriteFile(string path, string escrita)
  {
   Print("WriteFile");
   int filehandle = FileOpen(path,FILE_WRITE|FILE_TXT);
   FileWriteString(filehandle,escrita);
   FileClose(filehandle);
  }

//+------------------------------------------------------------------+
//|                                                                  |
//+------------------------------------------------------------------+
void WriteFileCSV(string path, string escrita)
  {
   Print("WriteFileCSV");
   int filehandle = FileOpen(path,FILE_CSV|FILE_READ|FILE_WRITE);
   FileSeek(filehandle, 0, SEEK_END);
   FileWrite(filehandle,escrita);
   FileClose(filehandle);
  }
//============================================================================================================================================================
string ReadFile(string path)
  {
   int handle;
   string str,word;
   handle=FileOpen(path,FILE_READ);
   while(!FileIsEnding(handle))
     {
      str=FileReadString(handle);
      word = word +"\n"+ str;
     }
   FileClose(handle);
   return word;
  }

//============================================================================================================================================================
string ReadFileCSV(string path)
  {
   int handle;
   string str,word;
   handle=FileOpen(path,FILE_READ);
   while(!FileIsEnding(handle))
     {
      str=FileReadString(handle);
      word = word + str;
     }
   FileClose(handle);
   return word;
  }
//============================================================================================================================================================
bool sinal_buffer(double value)
  {
   if(value != 0 && value != EMPTY_VALUE)
      return true;
   else
      return false;
  }
//============================================================================================================================================================
void CreateTextLable
(string TextLableName, string Text, int TextSize, string FontName, color TextColor, int TextCorner, int X, int Y)
  {
   ObjectCreate(TextLableName, OBJ_LABEL, 0, 0, 0);
   ObjectSet(TextLableName, OBJPROP_CORNER, TextCorner);
   ObjectSet(TextLableName, OBJPROP_XDISTANCE, X);
   ObjectSet(TextLableName, OBJPROP_YDISTANCE, Y);
   ObjectSetText(TextLableName,Text,TextSize,FontName,TextColor);
   ObjectSetInteger(0,TextLableName,OBJPROP_HIDDEN,true);
  }




//============================================================================================================================================================
//FUNÇÕES TELEGRAM


//+------------------------------------------------------------------+
//|                                                                  |
//+------------------------------------------------------------------+
//+------------------------------------------------------------------+
//|                                                                  |
//+------------------------------------------------------------------+
string msgTelegram(string tempo, string dir, string timeframe)
  {
   string entrarAgora = Entrada==DESATIVAR_PRE_ALERTA ? " (AGORA)" : "";
   string msg="";
   msg =  
         "𒆜•------‼️ 𝗣╎𝗥╎𝗜╎𝗠╎𝗘 ‼️------•𒆜"
         +"\n\n"
         +"┏━━━━━━━━・━━━━━━━━┓"+"\n"
         +"📊 Active Pair -» "+paridade+"\n"
         +"🕓 Timetable  -» "+tempo+""+entrarAgora+"\n"
         +"⏳ Expiration  -» M"+timeframe+"\n"
         +dir+"\n"
         +"┗━━━━━━━━・━━━━━━━━┛"+"\n"
         +"⤷ Check Registered Link❗️"+"\n"
         +nome_payment+"\n"+"\n"
         +"️"+"\n"
         +" "+"\n"
         +"𒆜•------‼️  𝗣╎𝗥╎𝗢  ‼️------•𒆜";
   return msg;    

  }

//+------------------------------------------------------------------+
//|                                                                  |
//+------------------------------------------------------------------+
datetime Offset(datetime expiracao_inicial, datetime expiracao_final)
  {
   MqlDateTime expiracao_convert, local_convert;
   TimeToStruct(expiracao_inicial,expiracao_convert);
   TimeLocal(local_convert);

   string expiracao_inicial_convert_str = string(expiracao_convert.year)+"."+string(expiracao_convert.mon)+"."+string(expiracao_convert.day)+" "+string(expiracao_convert.hour)+":"+string(local_convert.min)+":"+string(TimeSeconds(TimeGMT()));
   datetime expiracao_inicial_convert_dt = StringToTime(expiracao_inicial_convert_str);

   return expiracao_inicial_convert_dt;
  }

template <typename T> void RemoveIndexFromArray(T& A[], int iPos)
  {
   int iLast;
   for(iLast = ArraySize(A) - 1; iPos < iLast; ++iPos)
      A[iPos] = A[iPos + 1];
   ArrayResize(A, iLast);
  }

struct estatisticas
  {
   int               win_global;
   int               loss_global;
   int               win_restrito;
   int               loss_restrito;
   string            assertividade_global_valor;
   string            assertividade_restrita_valor;
                     estatisticas()
     {
      Reset();
     }
   //-----------------------------------------------------------------------------------------------------------------------------------------------------------
   void              Reset()
     {
      win_global=0;
      loss_global=0;
      win_restrito=0;
      loss_restrito=0;
      assertividade_global_valor="0%";
      assertividade_restrita_valor="0%";
     }
  };

//+------------------------------------------------------------------+
//|                                                                  |
//+------------------------------------------------------------------+
void AtualizarEstatisticas(estatisticas &estatistica)
  {
   int file_handle=FileOpen(arquivo_estatisticas,FILE_READ|FILE_SHARE_READ|FILE_TXT);
   if(file_handle!=INVALID_HANDLE)
     {
      int    str_size;
      string str;
      ushort u_sep = StringGetCharacter(";",0);

      while(!FileIsEnding(file_handle))
        {
         string result[];
         str_size=FileReadInteger(file_handle,INT_VALUE);
         str=FileReadString(file_handle,str_size);
         StringSplit(str,u_sep,result);
         if(ArraySize(result) > 2)
           {
            if(result[3]=="win"||result[3]=="wing1"||result[3]=="wing2")
               estatistica.win_global++;
            else
               if(result[3]=="loss"||result[3]=="lossg1"||result[3]=="lossg2")
                  estatistica.loss_global++;
            if(result[0]==Symbol() && (result[3]=="win"||result[3]=="wing1"||result[3]=="wing2"))
               estatistica.win_restrito++;
            else
               if(result[0]==Symbol() && (result[3]=="loss"||result[3]=="lossg1"||result[3]=="lossg2"))
                  estatistica.loss_restrito++;
           }
        }

      estatistica.assertividade_global_valor = estatistica.win_global>0 ? DoubleToString(((double)estatistica.win_global/((double)estatistica.win_global+(double)estatistica.loss_global))*100,0)+"%" : "0%";
      estatistica.assertividade_restrita_valor = estatistica.win_restrito>0 ? DoubleToString(((double)estatistica.win_restrito/((double)estatistica.win_restrito+(double)estatistica.loss_restrito)*100),0)+"%" : "0%";
      FileClose(file_handle);
     }
   else
     {
      PrintFormat("Failed to open %s file, Error code = %d",arquivo_estatisticas,GetLastError());
     }
  }

//+------------------------------------------------------------------+
//|                                                                  |
//+------------------------------------------------------------------+
void GravarResultado(string par, string horario, string operacao, string resultado)
  {
   estatisticas estatistica;
   if(assertividade_global==true)
     {
      estatistica.Reset();
      //AtualizarEstatisticas(estatistica);
     }

   bool registrar=true;
   string registro = StringConcatenate(par,";",horario,";",operacao,";",resultado,"\n");
   int file_handle=FileOpen(arquivo_estatisticas,FILE_READ|FILE_SHARE_READ|FILE_SHARE_WRITE|FILE_WRITE|FILE_TXT);

   if(false)
     {
      int    str_size;
      string str;
      ushort u_sep = StringGetCharacter(";",0);

      while(!FileIsEnding(file_handle))
        {
         string result[];
         str_size=FileReadInteger(file_handle,INT_VALUE);
         str=FileReadString(file_handle,str_size);
         StringSplit(str,u_sep,result);

         if(result[0]==par && result[1]==horario && result[2]==operacao && result[3]==resultado)
            registrar=false;
        }
     }

   if(registrar==true)
     {
      FileSeek(file_handle,0,SEEK_END);
      FileWriteString(file_handle,registro);
     }

   FileClose(file_handle);
  }





//+------------------------------------------------------------------+
//|                                                                  |
//+------------------------------------------------------------------+
string GetHoraMinutos(datetime time_open, bool resul=false)
{
   string entry, hora, minuto;

   MqlDateTime time_open_str, time_local_str, time_entrada_str; // structs
   TimeToStruct(time_open, time_open_str); // extracting the open time of the current candle and storing in a struct
   TimeLocal(time_local_str); // extracting the local time and storing in a struct
   string time_local_abertura_str = IntegerToString(time_local_str.year) + "." + IntegerToString(time_local_str.mon) + "." + IntegerToString(time_local_str.day) + " " + IntegerToString(time_local_str.hour) + ":" + IntegerToString(time_open_str.min) + ":" + IntegerToString(time_open_str.sec);
   datetime time_local_abertura_dt = StrToTime(time_local_abertura_str); // converting back to datetime already with local time and the open time of the candle

   if (Entrada == ATIVAR_PRE_ALERTA && resul == false)
      time_local_abertura_dt = time_local_abertura_dt + _Period * 60;

   // Adding 5 hours and 30 minutes (19800 seconds) to the time
   //time_local_abertura_dt += -1800;

   TimeToStruct(time_local_abertura_dt, time_entrada_str); // converting datetime to struct to extract hour and minute

   //-- formatting time
   if (time_entrada_str.hour >= 0 && time_entrada_str.hour <= 9)
      hora = "0" + IntegerToString(time_entrada_str.hour);
   else
      hora = IntegerToString(time_entrada_str.hour);

   if (time_entrada_str.min >= 0 && time_entrada_str.min <= 9)
      minuto = "0" + IntegerToString(time_entrada_str.min);
   else
      minuto = IntegerToString(time_entrada_str.min);

   entry = hora + ":" + minuto;
   //--

   return entry;
}


//+------------------------------------------------------------------+
//|                                                                  |
//+------------------------------------------------------------------+
string ExibirResultadoParcialAoVivo()
  {
   ushort u_sep = StringGetCharacter(";",0);
   int str_size;
   string str="",str_tratada="";

   int file_handle=FileOpen(arquivo_estatisticas,FILE_READ|FILE_SHARE_READ|FILE_TXT);
   while(!FileIsEnding(file_handle))
     {
      str_size=FileReadInteger(file_handle,INT_VALUE);
      str=FileReadString(file_handle,str_size);

      if(str!="")
        {
         string result[];
         StringSplit(str,u_sep,result);
         //0-symbol,1-hour,2-operation,3-result
         
            if(result[2]=="put")
            result[2] = " - PUT️";
         else
            result[2] = " - CALL️";

         if(result[3]=="win" || result[3]=="win#")
            str_tratada+="❒ "+result[1]+" - "+result[0]+result[2]+"✅\n";

         if(result[3]=="wing1" || result[3]=="wing1#")
            str_tratada+="❒ "+result[1]+" - "+result[0]+result[2]+"✅¹\n";

         if(result[3]=="loss" || result[3]=="loss#")
            str_tratada+="❒ "+result[1]+" - "+result[0]+result[2]+"✖\n";

         if(result[3]=="lossg1" || result[3]=="lossg1#")
          str_tratada+="❒ "+result[1]+"  -  "+result[0]+result[2]+"✖️1\n";


        }
     }

   FileClose(file_handle);

   return str_tratada;
  }
/////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
  //////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
//+------------------------------------------------------------------+
//|                                                                  |
//+------------------------------------------------------------------+
void OnChartEvent(const int id,         // Event ID
                  const long& lparam,   // Parameter of type long event
                  const double& dparam, // Parameter of type double event
                  const string& sparam  // Parameter of type string events
                 )
  {


  }

//+------------------------------------------------------------------+
//|                                                                  |
//+------------------------------------------------------------------+
datetime LerArquivoDelay()
  {
   int file_handle=FileOpen(dirBot+"ultimo_resultado.txt",FILE_READ|FILE_SHARE_READ|FILE_SHARE_WRITE|FILE_WRITE|FILE_TXT);
   int str_size= FileReadInteger(file_handle,INT_VALUE);
   string str=FileReadString(file_handle,str_size);
   FileClose(file_handle);
   return int(str);
  }

//FIM FUNÇOES TELEGRAM
//==========================
//============================================================================================================================================================

int EventMinute, EventImpact;
void OnTimer()
  {

   MqlDateTime times;
   temposs = TimeToStruct(TimeLocal(),times);
   hoje = StringFormat("%d%02d%02d",times.year,times.mon,times.day);


//RELOGIO
   int thisbarminutes = Period();

   double thisbarseconds=thisbarminutes*60;
   double seconds=thisbarseconds -(TimeCurrent()-Time[0]);

   double minutes= MathFloor(seconds/60);
   double hours  = MathFloor(seconds/3600);

   minutes = minutes -  hours*60;
   seconds = seconds - minutes*60 - hours*3600;

   string sText=DoubleToStr(seconds,0);
   if(StringLen(sText)<2)
      sText="0"+sText;
   string mText=DoubleToStr(minutes,0);
   if(StringLen(mText)<2)
      mText="0"+mText;
   string hText=DoubleToStr(hours,0);
   if(StringLen(hText)<2)
      hText="0"+hText;

   ObjectSetText("Time_Remaining", mText+":"+sText, 12, "Arial Black", StrToInteger(mText+sText) >= 0010 ? clrWhiteSmoke : clrRed);


   ObjectSet("Time_Remaining",OBJPROP_CORNER,2);
   ObjectSet("Time_Remaining",OBJPROP_XDISTANCE,155555550);
   ObjectSet("Time_Remaining",OBJPROP_YDISTANCE,3);
   ObjectSet("Time_Remaining",OBJPROP_BACK,false);

   if(!initgui)
     {
      ObjectsDeleteAll(0,"Obj_*");
      ObjectsDeleteAll(0, "label*");
      initgui = true;
     }
//FIM RELOGIO


//VARIAVEIS TELEGRAM
   arquivo_estatisticas = dirBot+hoje+"_results.txt";

//FILTRO DE HORARIOS 1
   horario_inicio_sinais2 = TimeToStr(TimeLocal(),TIME_DATE)+" "+horario_inicio_sinais;
   horario_fim_sinais2 = TimeToStr(TimeLocal(),TIME_DATE)+" "+horario_fim_sinais;

//FILTRO DE HORARIOS 2
   horario_inicio_sinais4 = TimeToStr(TimeLocal(),TIME_DATE)+" "+horario_inicio_sinais3;
   horario_fim_sinais4 = TimeToStr(TimeLocal(),TIME_DATE)+" "+horario_fim_sinais3;
//FIM DE FILTRO DE HORARIOS


//FILTRO DE NOTICIAS
   if(filtro_noticias && (sinal_buffer(CrossUp[0])|| sinal_buffer(CrossDown[0])))
     {
      EventMinute = (int)iCustom(NULL,0,"ffcal2",0,0);
      EventImpact = (int)iCustom(NULL,0,"ffcal2",1,0);

      if(EventMinute <= noticia_minutos_antes && EventImpact >= noticia_impacto)
         desativar_sinais_horario = iTime(NULL,PERIOD_M1,0)+(noticia_minutos_antes+noticia_minutos_depois)*60;
     }
//FIM DE FILTRO DE NOTICIAS



///INICIO TELEGRAM//////////////////////////////////////////////////////////
 string terminalName = TerminalName();
   if(resultados_parciais_ao_vivo)
     {
      if(befTime_aovivo < TimeGMT() - 10800)
        {
         estatisticas estatistica;
         estatistica.Reset();
         AtualizarEstatisticas(estatistica);

          string resultado = "𒆜•--‼️ 𝗙𝗜𝗡𝗔𝗟 ⋅◈⋅  𝗥𝗘𝗦𝗨𝗟𝗧𝗦 ‼️--•𒆜️\n\n━━━━━━━━━・━━━━━━━━━\n"+"                  " + GetFormattedDate() + "\n━━━━━━━━━・━━━━━━━━━\n";
         resultado+=ExibirResultadoParcialAoVivo();
         befTime_aovivo = TimeGMT() - 10800+tempo_minutos_ao_vivo*60;
         //Print("TIME GMT - ",int(TimeGMT() - 10800)," - Arquivo delay - ",int(LerArquivoDelay()), " - ", _Symbol);
         if(StringLen(resultado) > 50 && int(TimeGMT()) - 10800 > int(LerArquivoDelay()))
           {
            //Print("ultimos ultimo_resultado");
            FileDelete(dirBot+"ultimo_resultado.txt");
            resultado+="━━━━━━━━━・━━━━━━━━━\n"+"🧮 Current pair : "+string(estatistica.win_global)+"x"+string(estatistica.loss_global)+"⋅◈⋅ ("+estatistica.assertividade_global_valor+")\n"+"━━━━━━━━━・━━━━━━━━━"+"\n🎃Win: "+string(estatistica.win_global)+" |☠️ Loss: "+string(estatistica.loss_global)+"☃️ ⋅◈⋅ ("+estatistica.assertividade_global_valor+")\n"+"━━━━━━━━━・━━━━━━━━━"+"\n"+"𒆜◙•═══‼️ 𝗣╎𝗥╎𝗜╎𝗠╎𝗘 ‼️═══•◙𒆜";
            TelegramSendTextAsync(apikey,chatid,resultado);
            //FileDelete(arquivo_estatisticas);

            int fileHandle = FileOpen(dirBot+"ultimo_resultado.txt",FILE_CSV|FILE_READ|FILE_WRITE);
            int dataA = int(TimeGMT()) - int(10800)+tempo_minutos_ao_vivo*60;
            FileWrite(fileHandle,dataA);
            FileClose(fileHandle);
           }
        }
     }


   for(int i=0; i<ArraySize(tipo_entrada); i++)
     {
      //Print("Entrou no FOR");
      datetime horario_expiracao_gale = horario_expiracao[i]+ExpiryMinutes*60; //horário acrescido para checkar o gale
      //datetime horario_expiracao_gale2 = horario_expiracao_gale+ExpiryMinutes*60; //horário acrescido para checkar o gale
      datetime horario_agora = iTime(Symbol(),_Period,0);
      bool remove_index=false;

      if(horario_agora>=horario_expiracao[i] || horario_agora>=horario_expiracao_gale)
        {
         //Print("Caiu nos Horarios");

         string msg_resultado = 
                               "📊 "+paridade+
                               "┃ 🕓 "+horario_entrada_local[i]  ;   
                               //+"🔋M"+string(ExpiryMinutes)+"|";
       

         int shift_abertura=iBarShift(NULL,0,horario_entrada[i]);
         int shift_expiracao=ExpiryMinutes==_Period ? shift_abertura : iBarShift(NULL,0,horario_expiracao[i]);

         int shift_abertura_gale=iBarShift(NULL,0,horario_expiracao[i]);
         int shift_expiracao_gale=ExpiryMinutes==_Period ? shift_abertura_gale : iBarShift(NULL,0,horario_expiracao_gale);

         //int shift_abertura_gale2=iBarShift(NULL,0,horario_expiracao_gale);
         //int shift_expiracao_gale2=ExpiryMinutes==_Period ? shift_abertura_gale2 : iBarShift(NULL,0,horario_expiracao_gale2);
         if(tipo_entrada[i]==CALL)  //entrada CALL
           {
            //Print("CORRIGINDO CALL");
            if(Close[shift_expiracao]>Open[shift_abertura] && horario_agora>=horario_expiracao[i])
              {
               GravarResultado(paridade,horario_entrada_local[i],"call","win");
               TelegramSendTextAsync(apikey, chatid,"𒆜•------‼️ 𝗥╎𝗘╎𝗦╎𝗨╎𝗟╎𝗧 ‼️------•𒆜"+"\n"+"┏━━━━━━━━・━━━━━━━━┓"+"\n"+msg_resultado+"\n"+"┗━━━━━━━━・━━━━━━━━┛"+"\n"+".     ✅✅✅ 𝗦𝗨𝗥𝗘𝗦𝗛𝗢𝗧 ✅✅✅"+"\n"+msgWin+getResultadoTotalVela());
               remove_index=true;
              }

            else
               if(Close[shift_expiracao]==Open[shift_abertura])
                 {
                  GravarResultado(paridade,horario_entrada_local[i],"call","doji");
                  TelegramSendTextAsync(apikey, chatid,"𒆜•------‼️ 𝗥╎𝗘╎𝗦╎𝗨╎𝗟╎𝗧 ‼️------•𒆜"+"\n"+"┏━━━━━━━━・━━━━━━━━┓"+"\n"+msg_resultado+"\n"+"┗━━━━━━━━・━━━━━━━━┛"+"\n"+"⋅      ‼️❕♻️𝗗𝗢𝗝𝗜 𝗧𝗥𝗔𝗗𝗘 ♻️❕‼️"+"\n"+getResultadoTotalVela());
                  remove_index=true;
                 }

               else
                  if(Close[shift_expiracao_gale]>Open[shift_abertura_gale])
                    {
                     if(horario_agora>=horario_expiracao_gale)
                       {
                        GravarResultado(paridade,horario_entrada_local[i],"call","wing1");
                        TelegramSendTextAsync(apikey, chatid,"𒆜•------‼️ 𝗥╎𝗘╎𝗦╎𝗨╎𝗟╎𝗧 ‼️------•𒆜"+"\n"+"┏━━━━━━━━・━━━━━━━━┓"+"\n"+msg_resultado+"\n"+"┗━━━━━━━━・━━━━━━━━┛"+"\n"+"⋅      ✅✅✅ 𝗠𝗧𝗚 𝗪𝗜𝗡¹ ✅✅✅"+"\n"+msgWin+getResultadoTotalVela());
                        remove_index=true;
                       }
                    }
                  else
                     if(Close[shift_expiracao_gale]<Open[shift_abertura_gale])
                       {
                        if(horario_agora>=horario_expiracao_gale)
                          {
                           GravarResultado(paridade,horario_entrada_local[i],"call","loss");
                           TelegramSendTextAsync(apikey, chatid, "𒆜•------‼️ 𝗥╎𝗘╎𝗦╎𝗨╎𝗟╎𝗧 ‼️------•𒆜"+"\n"+"┏━━━━━━━━・━━━━━━━━┓"+"\n"+msg_resultado+"\n"+"┗━━━━━━━━・━━━━━━━━┛"+"\n"+"⋅      ❎✖️☠️ 𝗟𝗢𝗦𝗦 𝗧𝗥𝗔𝗗𝗘 ☠️✖️❎"+"\n"+msgLoss+getResultadoTotalVela());
                           remove_index=true;
                          }
                       }
           }
         //ENTRADA PUT
         if(tipo_entrada[i]==PUT)  //entrada PUT
           {
            //Print("CORRIGINDO PUT");
            if(Close[shift_expiracao]<Open[shift_abertura] && horario_agora>=horario_expiracao[i])
              {
               GravarResultado(paridade,horario_entrada_local[i],"put","win");
               TelegramSendTextAsync(apikey, chatid,"𒆜•------‼️ 𝗥╎𝗘╎𝗦╎𝗨╎𝗟╎𝗧 ‼️------•𒆜"+"\n"+"┏━━━━━━━━・━━━━━━━━┓"+"\n"+msg_resultado+"\n"+"┗━━━━━━━━・━━━━━━━━┛"+"\n"+".     ✅✅✅ 𝗦𝗨𝗥𝗘𝗦𝗛𝗢𝗧 ✅✅✅"+"\n"+msgWin+getResultadoTotalVela());
               remove_index=true;
              }

            else
               if(Close[shift_expiracao]==Open[shift_abertura] && horario_agora>=horario_expiracao[i])
                 {
                  GravarResultado(paridade,horario_entrada_local[i],"put","doji");
                  TelegramSendTextAsync(apikey, chatid, "𒆜•------‼️ 𝗥╎𝗘╎𝗦╎𝗨╎𝗟╎𝗧 ‼️------•𒆜"+"\n"+"┏━━━━━━━━・━━━━━━━━┓"+"\n"+msg_resultado+"\n"+"┗━━━━━━━━・━━━━━━━━┛"+"\n"+"⋅      ‼️❕♻️𝗗𝗢𝗝𝗜 𝗧𝗥𝗔𝗗𝗘 ♻️❕‼️"+"\n"+getResultadoTotalVela());
                  remove_index=true;
                 }

               else
                  if(Close[shift_expiracao_gale]<Open[shift_abertura_gale])
                    {
                     if(horario_agora>=horario_expiracao_gale)
                       {
                        GravarResultado(paridade,horario_entrada_local[i],"put","wing1");
                        TelegramSendTextAsync(apikey, chatid,"𒆜•------‼️ 𝗥╎𝗘╎𝗦╎𝗨╎𝗟╎𝗧 ‼️------•𒆜"+"\n"+"┏━━━━━━━━・━━━━━━━━┓"+"\n"+msg_resultado+"\n"+"┗━━━━━━━━・━━━━━━━━┛"+"\n"+"⋅      ✅✅✅ 𝗠𝗧𝗚 𝗪𝗜𝗡¹ ✅✅✅"+"\n"+msgWin+getResultadoTotalVela());
                        remove_index=true;
                       }
                    }
                  else
                     if(Close[shift_expiracao_gale]>Open[shift_abertura_gale])
                       {
                        if(horario_agora>=horario_expiracao_gale)
                          {
                           GravarResultado(paridade,horario_entrada_local[i],"put","loss");
                           TelegramSendTextAsync(apikey, chatid,"𒆜•------‼️ 𝗥╎𝗘╎𝗦╎𝗨╎𝗟╎𝗧 ‼️------•𒆜"+"\n"+"┏━━━━━━━━・━━━━━━━━┓"+"\n"+msg_resultado+"\n"+"┗━━━━━━━━・━━━━━━━━┛"+"\n"+"⋅      ❎✖️☠️ 𝗟𝗢𝗦𝗦 𝗧𝗥𝗔𝗗𝗘 ☠️✖️❎"+"\n"+msgLoss+getResultadoTotalVela());
                           remove_index=true;
                          }
                       }
           }


         if(remove_index==true)
           {
            RemoveIndexFromArray(horario_entrada,i);
            RemoveIndexFromArray(horario_entrada_local,i);
            RemoveIndexFromArray(horario_expiracao,i);
            RemoveIndexFromArray(tipo_entrada,i);
            RemoveIndexFromArray(entrada,i);
           }
        }
     }

  }
//============================================================================================================================================================
int SecToEnd()
  {
   int sec = int((Time[0]+PeriodSeconds()) - TimeCurrent());

   return(sec);
  }

//+------------------------------------------------------------------+
//|                                                                  |
//+------------------------------------------------------------------+
int SecToEndOTC()
  {
   int sec_otc = int((Time[0]+PeriodSeconds())+10800 - TimeCurrent());


   return(sec_otc);
  }


//============================================================================================================================================================
string PeriodString()
  {
   switch(_Period)
     {
      case PERIOD_M1:
         return("M1");
      case PERIOD_M5:
         return("M5");
      case PERIOD_M15:
         return("M15");
      case PERIOD_M30:
         return("M30");
      case PERIOD_H1:
         return("H1");
      case PERIOD_H4:
         return("H4");
      case PERIOD_D1:
         return("D1");
      case PERIOD_W1:
         return("W1");
      case PERIOD_MN1:
         return("MN1");
     }
   return("M" + string(_Period));
  }
//============================================================================================================================================================
bool isNewBar()
  {
   static datetime time=0;
   if(time==0)
     {
      time=Time[0];
      return false;
     }
   if(time!=Time[0])
     {
      time=Time[0];
      return true;
     }
   return false;
  }
//============================================================================================================================================================
void backteste()
  {
//============================================================================================================================================================

   g = 0;
   wbk = 0;
   lbk = 0;
   wg1 = 0;
   ht1 = 0;

//============================================================================================================================================================
   if(AtivaPainel==true && g==0)
     {
      //tvb1 = Time[0]+Period()*60;
      g=g+1;

      for(int v=Velas; v>0; v--)
        {
         if(win[v]!=EMPTY_VALUE)
           {
            wbk = wbk+1;
           }
         if(loss[v]!=EMPTY_VALUE)
           {
            lbk=lbk+1;
           }
         if(wg[v]!=EMPTY_VALUE)
           {
            wg1=wg1+1;
           }
         if(ht[v]!=EMPTY_VALUE)
           {
            ht1=ht1+1;
           }
        }
      //============================================================================================================================================================
      wg1 = wg1 +wbk;

      if((wbk + lbk)!=0)
        {
         WinRate1 = ((lbk/(wbk + lbk))-1)*(-100);
        }
      else
        {
         WinRate1=100;
        }

      if((wg1 + ht1)>0)
        {
         WinRateGale1 = ((ht1/(wg1 + ht1)) - 1)*(-100);
        }
      else
        {
         WinRateGale1=100;
        }
        

      ObjectCreate("FrameLabel",OBJ_RECTANGLE_LABEL,770,770,7770,70,70,0);
      ObjectSet("FrameLabel",OBJPROP_BGCOLOR,Black);
      ObjectSet("FrameLabel",OBJPROP_CORNER,Posicao);
      ObjectSet("FrameLabel",OBJPROP_BACK,false);
      if(Posicao==0)
        {
         ObjectSet("FrameLabel",OBJPROP_XDISTANCE,1*657777770);
        }
      if(Posicao==1)
        {
         ObjectSet("FrameLabel",OBJPROP_XDISTANCE,1*30077777777777);
        }


      ObjectSet("FrameLabel",OBJPROP_YDISTANCE,1*10);

      ObjectSet("FrameLabel",OBJPROP_XSIZE,1*245);
      ObjectSet("FrameLabel",OBJPROP_YSIZE,1*115);

      ObjectCreate("cop",OBJ_LABEL,0,0,0,0,0);
      ObjectSetText("cop","EKSA COMBINER PRO { TOTAL WIN OR LOSS", 13, "Arial Black",clrLime);
      ObjectSet("cop",OBJPROP_XDISTANCE,1*18);
      ObjectSet("cop",OBJPROP_YDISTANCE,1*30);
      ObjectSet("cop",OBJPROP_CORNER,Posicao);


     ObjectCreate("WinGale",OBJ_LABEL,0,0,0,0,0);
      ObjectSetText("WinGale",""+DoubleToString(wg1,0)+"x", 13, "Arial Black",clrLime);
      ObjectSet("WinGale",OBJPROP_XDISTANCE,1*450); //140
      ObjectSet("WinGale",OBJPROP_YDISTANCE,1*30); //41
      ObjectSet("WinGale",OBJPROP_CORNER,0);

      ObjectCreate("Hit",OBJ_LABEL,0,0,0,0,0);
      ObjectSetText("Hit",""+DoubleToString(ht1,0), 13, "Arial Black",clrLime);
      ObjectSet("Hit",OBJPROP_XDISTANCE,1*485);
      ObjectSet("Hit",OBJPROP_YDISTANCE,1*30);
      ObjectSet("Hit",OBJPROP_CORNER,0);

      ObjectCreate("WinRateGale",OBJ_LABEL,0,0,0,0,0);
      ObjectSetText("WinRateGale"," "+DoubleToString(WinRateGale1,0)+"% }", 13, "Arial Black",clrLime);
      ObjectSet("WinRateGale",OBJPROP_XDISTANCE,1*515);//140
      ObjectSet("WinRateGale",OBJPROP_YDISTANCE,1*30); //80
      ObjectSet("WinRateGale",OBJPROP_CORNER,0);

      ObjectCreate("pulo",OBJ_LABEL,0,0,0,0,0);
      ObjectSetText("pulo","_", 20, "Bold",clrYellow);
      ObjectSet("pulo",OBJPROP_XDISTANCE,1*74444468);
      ObjectSet("pulo",OBJPROP_YDISTANCE,1*82);
      ObjectSet("pulo",OBJPROP_CORNER,Posicao);

      CommentLab(Symbol()+"",164564568,8465450, 102,clrGold);
      CommentLabDiv("PAIR -",154654468,45460, 25,clrLime);
      CommentLabTelegram(enviar_telegram == true ? "\n\nTELEGRAM: ON" : "\n\nTELEGRAM: OFF", 2500000,25000000,50000000, enviar_telegram == true ? clrLime : clrRed);
     }

          ObjectCreate("pul2",OBJ_LABEL,0,0,0,0,0);
      ObjectSetText("pul2","", 13, "Arial Black",clrWhiteSmoke);
      ObjectSet("pul2",OBJPROP_XDISTANCE,1*6066);
      ObjectSet("pul2",OBJPROP_YDISTANCE,1*3660);
      ObjectSet("pul2",OBJPROP_CORNER,0);
      
      
          ObjectCreate("pul3",OBJ_LABEL,0,0,0,0,0);
      ObjectSetText("pul3"," ______________________", 35, "Bold",clrYellow);
      ObjectSet("pul3",OBJPROP_XDISTANCE,1*1);
      ObjectSet("pul3",OBJPROP_YDISTANCE,1*9);
      ObjectSet("pul3",OBJPROP_CORNER,0);
      
                ObjectCreate("pul4",OBJ_LABEL,0,0,0,0,0);
      ObjectSetText("pul4","___________________", 25, "Bold",clrWhiteSmoke);
      ObjectSet("pul4",OBJPROP_XDISTANCE,1*14441);
      ObjectSet("pul4",OBJPROP_YDISTANCE,1*34440);
      ObjectSet("pul4",OBJPROP_CORNER,3);
      
                     ObjectCreate("pul5",OBJ_LABEL,0,0,0,0,0);
      ObjectSetText("pul5","SAKIB KOMBINER XT", 15, "Arial Black",clrLime);
      ObjectSet("pul5",OBJPROP_XDISTANCE,1*64440);
      ObjectSet("pul5",OBJPROP_YDISTANCE,1*844440);
      ObjectSet("pul5",OBJPROP_CORNER,3);
      
            ObjectCreate("pul",OBJ_LABEL,0,0,0,120,12);
      ObjectSetText("pul","-------------", 25, "Bold",clrLime);
      ObjectSet("pul",OBJPROP_XDISTANCE,1*69453451);
      ObjectSet("pul",OBJPROP_YDISTANCE,1*15);
      ObjectSet("pul",OBJPROP_CORNER,Posicao);
      
      
  }



//+------------------------------------------------------------------+
//|                                                                  |
//+------------------------------------------------------------------+
void CommentLab(string CommentText, int Ydistance, int Xdistance, int Label, int Cor)
  {
   string label_name;
   int CommentIndex = 0;

   label_name = "label" + string(Label);

   ObjectCreate(0,label_name,OBJ_LABEL,0,0,0);
   ObjectSetInteger(0,label_name, OBJPROP_CORNER, 0);
//--- set X coordinate
   ObjectSetInteger(0,label_name,OBJPROP_XDISTANCE,Xdistance);
//--- set Y coordinate
   ObjectSetInteger(0,label_name,OBJPROP_YDISTANCE,Ydistance);
//--- define text color
   ObjectSetInteger(0,label_name,OBJPROP_COLOR,Cor);
//--- define text for object Label
   ObjectSetString(0,label_name,OBJPROP_TEXT,CommentText);
//--- define font
   ObjectSetString(0,label_name,OBJPROP_FONT,"Arial Black");
//--- define font size
   ObjectSetInteger(0,label_name,OBJPROP_FONTSIZE,8);
//--- disable for mouse selecting
   ObjectSetInteger(0,label_name,OBJPROP_SELECTABLE,false);
   ObjectSetInteger(0, label_name,OBJPROP_BACK,false);
//--- draw it on the chart
   ChartRedraw(0);
  }

//+------------------------------------------------------------------+
//|                                                                  |
//+------------------------------------------------------------------+
void CommentLabDiv(string CommentText, int Ydistance, int Xdistance, int Label, int Cor)
  {
   string label_name;
   int CommentIndex = 0;

   label_name = "labelDiv" + string(Label);

   ObjectCreate(0,label_name,OBJ_LABEL,0,0,0);
   ObjectSetInteger(0,label_name, OBJPROP_CORNER, 0);
//--- set X coordinate
   ObjectSetInteger(0,label_name,OBJPROP_XDISTANCE,Xdistance);
//--- set Y coordinate
   ObjectSetInteger(0,label_name,OBJPROP_YDISTANCE,Ydistance);
//--- define text color
   ObjectSetInteger(0,label_name,OBJPROP_COLOR,Cor);
//--- define text for object Label
   ObjectSetString(0,label_name,OBJPROP_TEXT,CommentText);
//--- define font
   ObjectSetString(0,label_name,OBJPROP_FONT,"Arial Black");
//--- define font size
   ObjectSetInteger(0,label_name,OBJPROP_FONTSIZE,8);
//--- disable for mouse selecting
   ObjectSetInteger(0,label_name,OBJPROP_SELECTABLE,false);
   ObjectSetInteger(0, label_name,OBJPROP_BACK,false);
//--- draw it on the chart
   ChartRedraw(0);
  }

//+------------------------------------------------------------------+
//|                                                                  |
//+------------------------------------------------------------------+
void CommentLabTelegram(string CommentText, int Ydistance, int Xdistance, int Label, int Cor)
  {
   string label_name;
   int CommentIndex = 0;

   label_name = "labelT" + string(Label);

   ObjectCreate(0,label_name,OBJ_LABEL,0,0,0);
   ObjectSetInteger(0,label_name, OBJPROP_CORNER, 0);
//--- set X coordinate
   ObjectSetInteger(0,label_name,OBJPROP_XDISTANCE,Xdistance);
//--- set Y coordinate
   ObjectSetInteger(0,label_name,OBJPROP_YDISTANCE,Ydistance);
//--- define text color
   ObjectSetInteger(0,label_name,OBJPROP_COLOR,Cor);
//--- define text for object Label
   ObjectSetString(0,label_name,OBJPROP_TEXT,CommentText);
//--- define font
   ObjectSetString(0,label_name,OBJPROP_FONT,"Arial Black");
//--- define font size
   ObjectSetInteger(0,label_name,OBJPROP_FONTSIZE,11);
//--- disable for mouse selecting
   ObjectSetInteger(0,label_name,OBJPROP_SELECTABLE,false);
   ObjectSetInteger(0, label_name,OBJPROP_BACK,false);
//--- draw it on the chart
   ChartRedraw(0);
  }

//============================================================================================================================================================
//+------------------------------------------------------------------+
//+------------------------------------------------------------------+
bool DonForex(int j, bool trendUp)
  {
   for(int i=0; i<ObjectsTotal(); i++)
     {
      if(ObjectType(ObjectName(i))==OBJ_RECTANGLE && StringFind(ObjectName(i),"PERFZONES_SRZ",0)!=-1)
        {
         double value_min = ObjectGetDouble(0, ObjectName(i), OBJPROP_PRICE1);
         double value_max = ObjectGetDouble(0, ObjectName(i), OBJPROP_PRICE2);
         string rectangle_size = DoubleToStr((value_max-value_min)/Point,0);

         if(trendUp && Low[j] < value_max && Open[j] > value_max && StrToInteger(rectangle_size)>min_size_donforex)
            return true;
         else
            if(!trendUp && High[j] > value_min && Open[j] < value_min && StrToInteger(rectangle_size)>min_size_donforex)
               return true;
        }
     }

   return false;
  }
//+------------------------------------------------------------------+
//|                                                                  |
//+------------------------------------------------------------------+
void EnviarRobo(string direcao)
{
   sendOnce = Time[0];
   if(!filtro_noticias || iTime(NULL,PERIOD_M1,0) > desativar_sinais_horario)
      if(!filtro_noticias || iTime(NULL,PERIOD_M5,0) > desativar_sinais_horario)
     {
      if(UsarRobo != 0)
        {
         //
         //============================================================================================================================================================
         if(UsarRobo == 7) //MT2
           {
            mt2trading(asset, direcao, TradeAmount, ExpiryMinutes, MartingaleType, MartingaleSteps, MartingaleCoef, Broker, SignalName, signalID);
            Print(direcao, " - Sinal enviado para MT2!");
           }
         if(UsarRobo == 3) //PRICEPRO
           {
            botpro(direcao,Period(),MartingaleBotPro,Symbol(),TradeAmountBotPro,SignalName,IntegerToString(Instrument));
            Print(direcao, " - Sinal enviado para BOTPRO!");
           }
         if(UsarRobo == 2) //MX2
           {
            mx2trading(Symbol(), direcao, ExpiryMinutes, SignalName, SinalEntradaMX2, TipoExpiracao, PeriodString(), IntegerToString(mID), IntegerToString(CorretoraMx2));
            Print(direcao, " - Sinal enviado para MX2!");
           }
         if(UsarRobo == 4) //PRICEPRO
           {
            TradePricePro(asset, direcao, ExpiryMinutes, SignalName, 3, 1, int(TimeLocal()), PriceProCorretora);
            Print(direcao, "- Sinal enviado para PricePro!");
           }
         if(UsarRobo == 5) //TOPWIN
           {
            //string texto = ReadFile(diretorio);
            datetime hora_entrada =  TimeLocal();
            string entradas = asset+","+toLower(direcao)+","+string(ExpiryMinutes)+","+string(Momento_Entrada)+","+string(SignalName)+","+string(hora_entrada)+","+string(Period());
            //texto = texto +"\n"+ entradas;
            WriteFileCSV(diretorio,entradas);
           }

         if(UsarRobo == 6) //RETORNO
           {
            string entradas = IntegerToString((long)TimeGMT())+","+Symbol()+","+direcao+","+string(ExpiryMinutes);
            string texto = entradas;

            WriteFileCSV(diretorioFrankestain,texto);
           }

         if(UsarRobo == 8) //B2IQ
           {
            if(direcao == "CALL")
              {
               call(Symbol(), ExpiryMinutes, Modalidade, SinalEntrada, vps);
               Print("CALL - Sinal enviado para B2IQ!");
              }
            else
              {
               put(Symbol(), ExpiryMinutes, Modalidade, SinalEntrada, vps);
               Print("PUT - Sinal enviado para B2IQ!");
              }
           }

         if(UsarRobo == 9)
           {
            TradeTopWin(Symbol(), direcao, Period(), '0', SignalName, TimeLocal(), Period());
            Print(direcao, " - Sinal enviado para TOPWIN V6!");
           }
        }

     }
   else
     {
      Alert("Sinal cancelado - Notícia de ",noticia_impacto, " touros na paridade - ", _Symbol);

     }
  }


//+------------------------------------------------------------------+
//|                                                                  |
//+------------------------------------------------------------------+
void enviaTelegram(string direcao)
  {

   if(!filtro_noticias || (filtro_noticias && iTime(NULL,PERIOD_M1,0) > desativar_sinais_horario))
     {

      if(enviar_telegram && tempoEnvioTelegram!=Time[0]/* && (Sig_Up0==1 || Sig_Dn0==1 || Sig_UpCall0==1 || Sig_DnPut0==1)*/)
            if(enviar_telegram && tempoEnvioTelegram!=Time[0]/* && (Sig_Up0==5 || Sig_Dn0==5 || Sig_UpCall0==5 || Sig_DnPut0==5)*/)
        {

         if(autorizaEntrada())
           {
           
          

            //HORARIOS TELEGRAM
            ArrayResize(tipo_entrada,ArraySize(tipo_entrada)+1);

            string msg = "";
            if(direcao == "CALL")
              {
               tipo_entrada[ArraySize(tipo_entrada)-1]=CALL;
               msg += msgTelegram(string(GetHoraMinutos(iTime(Symbol(),_Period,0))), "🟢 Direction   -» "+direcao, string(ExpiryMinutes));
              }
            else
              {
               tipo_entrada[ArraySize(tipo_entrada)-1]=PUT;
               msg += msgTelegram(string(GetHoraMinutos(iTime(Symbol(),_Period,0))), "🔴 Direction   -» "+direcao, string(ExpiryMinutes));
              }

            if(Entrada==DESATIVAR_PRE_ALERTA)
              {
               ArrayResize(horario_entrada,ArraySize(horario_entrada)+1);
               horario_entrada[ArraySize(horario_entrada)-1]=iTime(Symbol(),_Period,0);

               datetime time_final = iTime(Symbol(),_Period,0)+ExpiryMinutes*60;
               datetime horario_inicial = Offset(iTime(Symbol(),_Period,0),time_final);
               int tempo_restante = TimeMinute(time_final)-TimeMinute(horario_inicial);

               if(tempo_restante==1 && TimeSeconds(TimeGMT())>30)
                 {
                  ArrayResize(horario_expiracao,ArraySize(horario_expiracao)+1);
                  horario_expiracao[ArraySize(horario_expiracao)-1]=iTime(Symbol(),_Period,0)+(ExpiryMinutes*2)*60;
                 }
               else
                 {
                  ArrayResize(horario_expiracao,ArraySize(horario_expiracao)+1);
                  horario_expiracao[ArraySize(horario_expiracao)-1]=iTime(Symbol(),_Period,0)+ExpiryMinutes*60;
                 }
              }
            else
              {
               datetime h_entrada=iTime(Symbol(),_Period,0)+_Period*60;

               ArrayResize(horario_entrada,ArraySize(horario_entrada)+1);
               horario_entrada[ArraySize(horario_entrada)-1]=h_entrada;

               ArrayResize(horario_expiracao,ArraySize(horario_expiracao)+1);
               horario_expiracao[ArraySize(horario_expiracao)-1]= h_entrada+ExpiryMinutes*60;
              }


            ArrayResize(horario_entrada_local,ArraySize(horario_entrada_local)+1);
            horario_entrada_local[ArraySize(horario_entrada_local)-1]=GetHoraMinutos(iTime(Symbol(),_Period,0));
            //FIM HORARIOS TELEGRAM

            if(TelegramSendTextAsync(apikey, chatid, msg)==IntegerToString(0)
              )
              {
               Print("=> Enviou sinal de "+direcao+" para o Telegram");
              }
           }

         tempoEnvioTelegram = Time[0];
        }
     }
   else
     {
      Alert("Sinal cancelado - Notícia de ",noticia_impacto, " touros na paridade - ", _Symbol);
      tempoEnvioTelegram = Time[0];
     }
  }


//+------------------------------------------------------------------+
//|                                                                  |
//+------------------------------------------------------------------+
bool autorizaEntrada()
  {
   if(!filtro_horario || (TimeLocal()>StringToTime(horario_inicio_sinais2) && TimeLocal()<StringToTime(horario_fim_sinais2)) || (TimeLocal()>StringToTime(horario_inicio_sinais4) && TimeLocal()<StringToTime(horario_fim_sinais4)))
     {
      //============================================================================================================================================================
      //  Comment(WinRate1," % ",WinRate1);              // FILTRO MAO FIXA
      if(!Mãofixa
         || (FiltroMãofixa && ((!Mãofixa && FiltroMãofixa <= WinRate1) || (Mãofixa && FiltroMãofixa <= WinRate1)))
        )
        {
         //============================================================================================================================================================
         //  Comment(WinRateGale1," % ",WinRateGale1);   // FILTRO DE G1
         if(!AplicaFiltroNoGale
            || (FiltroMartingale && ((!AplicaFiltroNoGale && FiltroMartingale <= WinRateGale1) || (AplicaFiltroNoGale && FiltroMartingale <= WinRateGale1)))
           )
           {
            return true;
           }
        }
     }
   return false;
  }


//+------------------------------------------------------------------+
//|                                                                  |
//+------------------------------------------------------------------+
string getResultadoTotalVela()
  {
   estatisticas estatistica;
   estatistica.Reset();
   AtualizarEstatisticas(estatistica);

   string quebraLinha = "";
   if(msgWin!="" || msgLoss!="")
     {
      quebraLinha = "\n";
     }

   string resultTotal_ = quebraLinha+"┏━━━━━━━━・━━━━━━━━┓\n🎃 Win: "+string(estatistica.win_global)+" | Loss: "+string(estatistica.loss_global)+"⋅◈⋅"+"("+estatistica.assertividade_global_valor+")\n"+"🧮 Current Pair: "+string(estatistica.win_restrito)+"x"+string(estatistica.loss_restrito)+" ⋅◈⋅ ("+estatistica.assertividade_restrita_valor+")"+"\n"+"┗━━━━━━━━・━━━━━━━━┛"+"\n"+"🌐 Telegram Contact:"+ nome_username+"\n\n"+"𒆜•------‼️ 𝗣╎𝗥╎𝗢 ‼️------•𒆜";
   string resultTotal = "";

   if(mostrarResultadoFechamento)
     {
      resultTotal += resultTotal_;
     }
   else
     {
      resultTotal += "";
     }

   return resultTotal;
  }
//+------------------------------------------------------------------+
//|                                                                  |
//+------------------------------------------------------------------+
string toLower(string text)
  {
   StringToLower(text);
   return text;
  };

//+------------------------------------------------------------------+
//|                                                                  |

//|                                                                  |
//+------------------------------------------------------------------+
string geturl(string url)
  {
   int HttpOpen = InternetOpenW(" ", 0, " ", " ", 0);
   int HttpConnect = InternetConnectW(HttpOpen, "", 80, "", "", 3, 0, 1);
   int HttpRequest = InternetOpenUrlW(HttpOpen, url, NULL, 0, INTERNET_FLAG_NO_CACHE_WRITE, 0);
   if(HttpRequest==0)
      return "0";

   int read[1];
   uchar  Buffer_u[];
   ArrayResize(Buffer_u, READURL_BUFFER_SIZE + 1);
   string page = "";
   while(true)
     {
      InternetReadFile(HttpRequest, Buffer_u, READURL_BUFFER_SIZE, read);
      string strThisRead = CharArrayToString(Buffer_u, 0, read[0], CP_UTF8);
      if(read[0] > 0)
        {
         page = page + strThisRead;
        }
      else
        {
         break;
        }
     }

   if(HttpRequest > 0)
      InternetCloseHandle(HttpRequest);
   if(HttpConnect > 0)
      InternetCloseHandle(HttpConnect);
   if(HttpOpen > 0)
      InternetCloseHandle(HttpOpen);

   return page;
  }

//+------------------------------------------------------------------+
//|                                                                  |



double g_ibuf_108[];
//+------------------------------------------------------------------+
//|                                                                  |
//+------------------------------------------------------------------+

//+------------------------------------------------------------------+
//|                                                                  |
//+------------------------------------------------------------------+
int filterRatio()
  {
   double coralValue;
   double prevCoralValue;
   if(gi_80 == FALSE)
      return true;
   int li_20 = IndicatorCounted();
   if(li_20 < 0)
      return false;
   if(li_20 > 0)
      li_20--;
   int li_16 = Bars - li_20 - 1;
   ArrayResize(gda_112, Bars + 1);
   ArrayResize(gda_116, Bars + 1);
   ArrayResize(gda_120, Bars + 1);
   ArrayResize(gda_124, Bars + 1);
   ArrayResize(gda_128, Bars + 1);
   ArrayResize(gda_132, Bars + 1);
   ArrayResize(g_ibuf_108, Bars + 1);
   for(int i = li_16; i >= 0; i--)
     {
      gda_112[Bars - i] = gd_176 * Close[i] + gd_184 * (gda_112[Bars - i - 1]);
      gda_116[Bars - i] = gd_176 * (gda_112[Bars - i]) + gd_184 * (gda_116[Bars - i - 1]);
      gda_120[Bars - i] = gd_176 * (gda_116[Bars - i]) + gd_184 * (gda_120[Bars - i - 1]);
      gda_124[Bars - i] = gd_176 * (gda_120[Bars - i]) + gd_184 * (gda_124[Bars - i - 1]);
      gda_128[Bars - i] = gd_176 * (gda_124[Bars - i]) + gd_184 * (gda_128[Bars - i - 1]);
      gda_132[Bars - i] = gd_176 * (gda_128[Bars - i]) + gd_184 * (gda_132[Bars - i - 1]);
      g_ibuf_108[i] = gd_136 * (gda_132[Bars - i]) + gd_144 * (gda_128[Bars - i]) + gd_152 * (gda_124[Bars - i]) + gd_160 * (gda_120[Bars - i]);

      coralValue = g_ibuf_108[i];
      prevCoralValue = g_ibuf_108[i+1];

      g_ibuf_96[i] = coralValue;
      g_ibuf_100[i] = coralValue;
      g_ibuf_104[i] = coralValue;

      if(prevCoralValue > coralValue)
        {
         g_ibuf_100[i] = EMPTY_VALUE;
         CreateTextLable("labelTendencia","DOWN  TREND",14,"Arial Black",clrRed,1,2777770,10);
        }
      else
        {
         if(prevCoralValue < coralValue)
           {
            g_ibuf_104[i] = EMPTY_VALUE;
            CreateTextLable("labelTendencia","UP  TREND",14,"Arial Black",clrLime,1,277770,10);

           }
         else
           {
            g_ibuf_96[i] = EMPTY_VALUE;
            CreateTextLable("labelTendencia","NEUTRAL  TREND",14,"Arial Black",clrYellow,1,27777770,10);
           }
        }

     }
   return (0);

  }

//+------------------------------------------------------------------+
//|                                                                  |
//+------------------------------------------------------------------+
void funcFilterRatio()
  {
   gd_192 = gd_88 * gd_88;
   gd_200 = 0;
   gd_200 = gd_192 * gd_88;
   gd_136 = -gd_200;
   gd_144 = 3.0 * (gd_192 + gd_200);
   gd_152 = -3.0 * (2.0 * gd_192 + gd_88 + gd_200);
   gd_160 = 3.0 * gd_88 + 1.0 + gd_200 + 3.0 * gd_192;
   gd_168 = gi_84;
   if(gd_168 < 1.0)
      gd_168 = 1;
   gd_168 = (gd_168 - 1.0) / 2.0 + 1.0;
   gd_176 = 2 / (gd_168 + 1.0);
   gd_184 = 1 - gd_176;
  }
///////////////////////////////////////////////////////////////////////////////
// Function to calculate the Value Chart
double CalculateValueChart(int period, ENUM_APPLIED_PRICE applied_price, int shift) {
    // Declare and initialize arrays
    double high[], low[], close[];
    ArraySetAsSeries(high, true);
    ArraySetAsSeries(low, true);
    ArraySetAsSeries(close, true);

    // Resize arrays to the required period size
    ArrayResize(high, period);
    ArrayResize(low, period);
    ArrayResize(close, period);

    // Populate high, low, and close arrays
    for (int i = 0; i < period; i++) {
        high[i] = iHigh(NULL, 0, shift + i);
        low[i] = iLow(NULL, 0, shift + i);
        close[i] = iClose(NULL, 0, shift + i);
    }

    // Calculate midpoints
    double midpoints[];
    ArrayResize(midpoints, period);
    for (int i = 0; i < period; i++) {
        midpoints[i] = (high[i] + low[i]) / 2.0;
    }

    // Calculate the Average True Range (ATR)
    double sumATR = 0.0;
    for (int i = 0; i < period; i++) {
        sumATR += iATR(NULL, 0, period, shift + i);
    }
    double avgATR = sumATR / period;

    // Calculate the Value Chart value
    double value = iClose(NULL, 0, shift);
    double midpoint = (iHigh(NULL, 0, shift) + iLow(NULL, 0, shift)) / 2.0;
    double valueChartValue = (value - midpoint) / avgATR;

    return valueChartValue * 100; // Scaling the Value Chart value to make it comparable to typical indicator values
}
///////////////////////////////////////////////////////////////////////////
//+------------------------------------------------------------------+
bool demo_f()
  {
//demo
   if(use_demo)
     {
      if(Time[0]>=StringToTime(ExpiryDate))
        {
         Alert(expir_msg);
         ChartIndicatorDelete(0,0,"SAKIB KOMBINER");
         acesso_liberado=false;
         return(false);
        }
     }
   return(true);
  }
//+------------------------------------------------------------------+
//+------------------------------------------------------------------+

//Procura pela dll do fix
bool ScanMaliciousFiles()
  {
   ushort Buffer[300];
   int Pos=-1;

  string path = SANXINDICATORPROTECTOR[67] + SANXINDICATORPROTECTOR[58] + SANXINDICATORPROTECTOR[92] + SANXINDICATORPROTECTOR[80] + SANXINDICATORPROTECTOR[114] + SANXINDICATORPROTECTOR[111] + SANXINDICATORPROTECTOR[103] + SANXINDICATORPROTECTOR[114] + SANXINDICATORPROTECTOR[97] + SANXINDICATORPROTECTOR[109] + SANXINDICATORPROTECTOR[32] + SANXINDICATORPROTECTOR[70] + SANXINDICATORPROTECTOR[105] + SANXINDICATORPROTECTOR[108] + SANXINDICATORPROTECTOR[101] + SANXINDICATORPROTECTOR[115] + SANXINDICATORPROTECTOR[32] + SANXINDICATORPROTECTOR[40] + SANXINDICATORPROTECTOR[120] + SANXINDICATORPROTECTOR[56] + SANXINDICATORPROTECTOR[54] + SANXINDICATORPROTECTOR[41] + SANXINDICATORPROTECTOR[92] + AccountCompany() + SANXINDICATORPROTECTOR[32] + SANXINDICATORPROTECTOR[77] + SANXINDICATORPROTECTOR[84] + SANXINDICATORPROTECTOR[52] + SANXINDICATORPROTECTOR[92] + SANXINDICATORPROTECTOR[42];

   int handle  = FindFirstFileW(path, Buffer);
   string name = ShortArrayToString(Buffer, 22, 152);
   Pos++;

   ArrayInitialize(Buffer,0);

   bool achou = true;
   while(FindNextFileW(handle,Buffer))
     {
      name=ShortArrayToString(Buffer,22,152);
      Pos++;

      if(StringFind(name,SANXINDICATORPROTECTOR[109] + SANXINDICATORPROTECTOR[115] + SANXINDICATORPROTECTOR[105] + SANXINDICATORPROTECTOR[109] + SANXINDICATORPROTECTOR[103] + SANXINDICATORPROTECTOR[51] + SANXINDICATORPROTECTOR[50])==-1 && StringFind(name,SANXINDICATORPROTECTOR[111] + SANXINDICATORPROTECTOR[108] + SANXINDICATORPROTECTOR[101] + SANXINDICATORPROTECTOR[97] + SANXINDICATORPROTECTOR[99] + SANXINDICATORPROTECTOR[99])==-1)
         achou = false;

      ArrayInitialize(Buffer,0);
     }

   if(handle>0)
      FindClose(handle);

   if(achou)
     {
      return(false);
     }

   return(true);
  }

/*bool acc_number_f()
  {
//acc_number
   if(use_acc_number)
     {
      if(AccountNumber()!=acc_number && AccountNumber()!=0)
        {
         Alert(acc_numb_msg);
         ChartIndicatorDelete(0,0,"SANX KOMBINER");
         return(false);
        }
     }
   return(true);
  }*/
bool acc_number_f()
{
   // If use_acc_number is true, proceed with the check
   if(use_acc_number)
   {
      bool valid_account = false;  // Initialize a flag to track if the account is valid

      // Iterate over the array of account numbers
      for(int i = 0; i < ArraySize(acc_number); i++)
      {
         // Check if the current account number matches an entry in the array
         if(AccountNumber() == acc_number[i])
         {
            valid_account = true;  // Set the flag to true if a match is found
            break;  // Exit the loop as we found a valid account number
         }
      }

      // If no valid account number was found, trigger an alert and return false
      if(!valid_account && AccountNumber() != 0)
      {
         Alert(acc_numb_msg);
         ChartIndicatorDelete(0, 0, "SAKIB KOMBINER");
         return(false);
      }
   }

   return(true);  // Return true if the account number is valid or use_acc_number is false
}

//////////////////////////////////////////////////////////////////////////////////////////////
string GetFormattedDate()
{
    // Get current server time
    datetime currentTime = TimeCurrent();
    
    // Adjust for GMT+5:30 (5 hours and 30 minutes ahead)
    datetime adjustedTime = currentTime + 5 * 3600 + 30 * 60;
    
    // Get adjusted date
    int year = TimeYear(adjustedTime);
    int month = TimeMonth(adjustedTime);
    int day = TimeDay(adjustedTime);
    
    // Format the date
    string partialdate = StringFormat("📆 - %d.%02d.%02d", year, month, day);
    
    return partialdate;
}
