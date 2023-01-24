# ETL & ELT
> 최근 큰 data를 사용하기가 편리해 짐에 따라 extract를 한 뒤에 바로 DW나 data lake에 load가 되고
> 그 이후에 user가 사용을 요청을 할 경우 그 때서야 transformation이 일어나도록 하는 ELT가 고려 중이다.

## ETL (Extract Transform load)

![ETL](https://user-images.githubusercontent.com/105041834/210353028-5305d818-0773-4b95-99cd-05ff9e9dfde6.jpg)

- Advantages
  - Greater Compliance (Transformation이 일어난 후 DW에 넣어지기 때문에 security 보장)
    - Safeguard private data before putting the data in the DW
  - Reduced Storage Costs
    - Only store needed data -> save storage costs

- Disadvantages
  - Data analysts들의 특정 요구에 따라 transformation이 결정 된다.
    - 이로 인해 pipeline을 관리하는 사람이 필요하다.

## ELT

![ELT](https://user-images.githubusercontent.com/105041834/210353040-6fc5c174-dda9-4a5e-a27f-630bf68f6ffb.jpg)

- Advantages
  - Greater Flexibility (transformation이 일어나지 않고 저장)
  - Simplicity (Use SQL DB built-in capabilities)
  - Rapid Data ingestion (Do not need to wait for data)
  - Transform Only the Data you Need (특정 data를 targeting 해서 수정한다.)
- Disadvantages
  - More Vulnerable to Risk
  - Less Established (아직 발전이 더디다.)




## Reference
- [Reference](https://www.cdata.com/blog/data_connectivity/20210706-etl-vs-elt?kw=&cpn=2023385644&utm_source=google&utm_medium=cpc&utm_campaign=CData_-_Search_-_Branding_-_DSA&utm_content=Branding_-_DSA&utm_term=|&kw=&cpn=2023385644&gclid=CjwKCAiAwc-dBhA7EiwAxPRylIIPUqIWfZycvqtjBHhuA0pPSPycF5utzmrD4JdDER5r1-bXd2XdjxoC0GEQAvD_BwE)