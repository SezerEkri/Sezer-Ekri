#include <stdio.h>
#include <stdlib.h>

int main(int argc, char *argv[]) {
	int cesit, yedek, yedek1, yedek2, sirtcantasi, i, i1, adet=0, toplam;
	float sirtcantasi1, agirlik;
	
	printf("Kac cesit esya gireceksiniz?:\t");
	scanf("%d", &cesit);
	
	int matris[cesit][3];
	
	for(i=0; i<cesit; i++){ ////////////////////////////////////////////// MATRİSLERİ SIFIRLIYOEUZ.
		for(i1=0; i1<2; i1++)
		matris[i][i1]=0;
	}
	for(i=0;i<cesit;i++){ //////////////////////////////////////////////// ADET SAYISINI ARTIRIYOR.
		matris[i][2]=i+1;
	}
	for(i=0; i<cesit; i++){ ////////////////////////////////////////////// AĞIRLIK VE DEĞER SAYILARI GİRİLİYOR.
		printf("%d. esyanin agirligi:\t", i+1); scanf("%f", &agirlik);
		matris[i][0]=agirlik*10; ///////////////////////////////////////// AĞIRLIĞI 10 İLE ÇARPIP FLOAT OLAN DEĞERLERİ İNTİGER YAPIYOR.
		printf("%d. esyanin degeri:\t", i+1); scanf("%d", &matris[i][1]);
		
		for(i1=0; i1<i; i1++){ /////////////////////////////////////////// BİRİM FİYATLARINA GÖRE EN DEĞERLİ EŞYALARI BÜYÜKTEN KÜÇÜĞE SIRALIYOR.
			if(matris[i][0]<10){
			if(matris[i][1]/(matris[i][0])>matris[i1][1]/(matris[i1][0])){
				yedek= matris[i][0];
				yedek1= matris[i][1];
				yedek2= matris[i][2];
				matris[i][0]=matris[i1][0];
				matris[i][1]=matris[i1][1];
				matris[i][2]=matris[i1][2];
				matris[i1][0]=yedek;
				matris[i1][1]=yedek1;
				matris[i1][2]=yedek2;
			}
		  }
	    }
     }		
	printf("Sirtcantasi Kapasitesini Giriniz:\t"); 
	scanf("%f", &sirtcantasi1);
	sirtcantasi=sirtcantasi1*10; /////////////////////////////////////////// AĞIRLIĞI 10 İLE ÇARPMIŞTIK. SIRT ÇANTASINI DA 10 İLE ÇARPIP İNTİGER'A ÇEVİRİYORUZ.
	printf("=============================================================\n");

	printf("En iyi Urun Listesi:\n");
	for(i=0;i<cesit;i++){ ////////////////////////////////////////////////// ÇANTADA KALAN BOŞLUĞU BULUYOR.
		for(;sirtcantasi>=matris[i][0];adet++){
			sirtcantasi=sirtcantasi-matris[i][0];
			if(sirtcantasi<matris[i][0]){ ///////////////////////////////// EN DEĞERLİ OLANDAN BAŞLAYIP ÇANTAYA EKLİYOR. SONRA DİĞERİNE GEÇİYOR.
				adet++;
				if(sirtcantasi>=matris[i][0]-1)
				adet++;
				printf("%d. Esya Adeti :\t%d\n", matris[i][2], adet);
				toplam=toplam + adet*matris[i][1];
				adet=0;
			}
		}
	}
	printf("TOPLAM FIYAT=\t %dTL", toplam);
	return 0; 
}
