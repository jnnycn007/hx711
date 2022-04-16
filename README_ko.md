[English](/README.md) | [ 简体中文](/README_zh-Hans.md) | [繁體中文](/README_zh-Hant.md) | [日本語](/README_ja.md) | [Deutsch](/README_de.md) | [한국어](/README_ko.md)

<div align=center>
<img src="/doc/image/logo.png"/>
</div>

## LibDriver HX711

[![MISRA](https://img.shields.io/badge/misra-compliant-brightgreen.svg)](/misra/README.md) [![API](https://img.shields.io/badge/api-reference-blue.svg)](https://www.libdriver.com/docs/hx711/index.html) [![License](https://img.shields.io/badge/license-MIT-brightgreen.svg)](/LICENSE)

HX711은 Haixin 기술 집적 회로의 특허 기술을 채택한 고정밀 전자 저울을 위해 특별히 설계된 24비트 A/D 변환기 칩입니다. 같은 유형의 다른 칩과 비교할 때 칩셋은 더 안정적입니다. 고집적, 빠른 응답 및 강력한 간섭 방지의 장점이 있습니다. 그것은 전자 밀도를 감소시킵니다. 저울의 전체 비용은 전체 기계의 성능과 신뢰성을 향상시킵니다.

LibDriver HX711은 LibDiver에서 출시한 HX711의 전체 기능 드라이버입니다. 차등 광고 읽기 기능을 제공합니다. LibDriver는 MISRA를 준수합니다.

### 콘텐츠

  - [설명](#설명)
  - [설치](#설치)
  - [사용](#사용)
    - [example basic](#example-basic)
  - [문서](#문서)
  - [기고](#기고)
  - [저작권](#저작권)
  - [문의하기](#문의하기)

### 설명

/src 디렉토리에는 LibDriver HX711의 소스 파일이 포함되어 있습니다.

/interface 디렉토리에는 LibDriver HX711용 플랫폼 독립적인 gpio 버스 템플릿이 포함되어 있습니다.

/test 디렉토리에는 LibDriver HX711드라이버 테스트 프로그램이 포함되어 있어 칩의 필요한 기능을 간단히 테스트할 수 있습니다.

/example 디렉토리에는 LibDriver HX711 프로그래밍 예제가 포함되어 있습니다.

/doc 디렉토리에는 LibDriver HX711오프라인 문서가 포함되어 있습니다.

/datasheet 디렉토리에는 HX711 데이터시트가 있습니다.

/project 디렉토리에는 일반적으로 사용되는 Linux 및 마이크로컨트롤러 개발 보드의 프로젝트 샘플이 포함되어 있습니다. 모든 프로젝트는 디버깅 방법으로 셸 스크립트를 사용하며, 자세한 내용은 각 프로젝트의 README.md를 참조하십시오.

### 설치

/interface 디렉토리에서 플랫폼 독립적인 gpio 버스 템플릿을 참조하여 지정된 플랫폼에 대한 gpioI 버스 드라이버를 완성하십시오.

/src 디렉토리, /interface 디렉토리 및 /example 디렉토리를 프로젝트에 추가하십시오.

### 사용

#### example basic

```C
uint8_t res;
uint8_t i;
int32_t raw_voltage;
double voltage_v;

res = hx711_basic_init();
if (res != 0)
{
    return 1;
}

...

for (i = 0; i < 3; i++)
{
    res = hx711_basic_read((int32_t *)&raw_voltage, (double *)&voltage_v);
    if (res != 0)
    {
        (void)hx711_basic_deinit();

        return 1;
    }
    hx711_interface_delay_ms(1000);
    hx711_interface_debug_print("hx711: raw voltage is %d.\n", raw_voltage);
    hx711_interface_debug_print("hx711: voltage is %fmV.\n", voltage_v); 

    ...
    
}

...

(void)hx711_basic_deinit();

return 0;
```

### 문서

온라인 문서: https://www.libdriver.com/docs/hx711/index.html

오프라인 문서: /doc/html/index.html

### 기고

연락주세요lishifenging@outlook.com

### 저작권

저작권 (c) 2015 - 지금 LibDriver 판권 소유

MIT 라이선스(MIT)

이 소프트웨어 및 관련 문서 파일("소프트웨어")의 사본을 얻은 모든 사람은 이에 따라 무제한 사용, 복제, 수정, 통합, 출판, 배포, 2차 라이선스를 포함하여 소프트웨어를 처분할 수 있는 권리가 부여됩니다. 소프트웨어의 사본에 대한 라이선스 및/또는 판매, 그리고 소프트웨어가 위와 같이 배포된 사람의 권리에 대한 2차 라이선스는 다음 조건에 따릅니다.

위의 저작권 표시 및 이 허가 표시는 이 소프트웨어의 모든 사본 또는 내용에 포함됩니다.

이 소프트웨어는 상품성, 특정 목적에의 적합성 및 비침해에 대한 보증을 포함하되 이에 국한되지 않는 어떠한 종류의 명시적 또는 묵시적 보증 없이 "있는 그대로" 제공됩니다. 어떤 경우에도 저자 또는 저작권 소유자는 계약, 불법 행위 또는 기타 방식에 관계없이 소프트웨어 및 기타 소프트웨어 사용으로 인해 발생하거나 이와 관련하여 발생하는 청구, 손해 또는 기타 책임에 대해 책임을 지지 않습니다.

### 문의하기

연락주세요lishifenging@outlook.com