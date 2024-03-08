<table border="1">
    <tr>
        <td colspan="2" align="center">
            SALES_STAFF
        </td>
    </tr>
    <tr>
        <td rowspan="6">
            POSITION_NAME<br>
            name
        </td>
        <td>
            SALES_TERRITORY<br>
            name
        </td>
    </tr>
    <tr>
        <td>
            COUNTRY<br>
            name
        </td>
    </tr>
    <tr>
        <td>
            REGION<br>
            name
        </td>
    </tr>
    <tr>
        <td>
            CITY<br>
            name
        </td>
    </tr>
    <tr>
        <td>
            POSTAL_ZONE<br>
            zone
        </td>
    </tr>
    <tr>
        <td>
            ADDRESS<br>
            address1, address2
        </td>
    </tr>
    <tr>
        <td colspan="2">
            EMPLOYEE<br>
            <strong>
                <u>
                    sales_staff_code
                </u>
            </strong>, first_name, last_name, extension, work_phone, fax, email, date_hired
        </td>
    </tr>
</table>

Een `POSITION_NAME` (zoals verkoper) kan bij meerdere `SALES_TERRITORY` horen. Er zijn namelijk verkopers in meerdere territoria. Ook heeft een territorium werknemers op verschillende posities. Dus deze moeten naast elkaar komen te staan.

In een `SALES_TERRITORY` zitten meerdere `COUNTRY`, maar een land valt maar onder 1 territorium. Dus moet `SALES_TERRITORY` moet boven `COUNTRY` staan.

Dezelfde logica geldt voor de andere kolommen die eronder staan. `address1` en `address2` staan in 1 vakje omdat die een 1-op-1 relatie hebben.

Onderaan staan alle attributen die gewoon bij een enkele rij horen van de tabel.

<table border="1">
    <tr>
        <td colspan="5" align="center">
            PRODUCT
        </td>
    </tr>
    <tr>
        <td rowspan="2">
            LANGUAGE<br>
            name
        </td>
        <td rowspan="2">
            PRODUCTION_COST<br>
            cost
        </td>
        <td rowspan="2">
            MARGIN<br>
            percentage
        </td>
        <td rowspan="2">
            INTRODUCTION_DATE<br>
            date
        </td>
        <td>
            PRODUCT_LINE<br>
            code, name
        </td>
    </tr>
    <tr>
        <td style="border-left: 1px solid black;">
            PRODUCT_TYPE_EN<br>
            name
        </td>
    </tr>
    <tr>
        <td colspan="5">
            PRODUCT<br>
            <strong>
                <u>
                    id
                </u>
            </strong>, product_image, name, description
        </td>
    </tr>
</table>

Bij de bovenstaande tabel zijn er veel, veel-op-veel relaties.

Afgeleide dimensiewaarde:

`PRODUCT_SALE_PRICE` = `PRODUCTION_COST` * `MARGIN` + `PRODUCTION_COST`

<table border="1">
    <tr>
        <td align="center">
            DATE
        </td>
    </tr>
    <tr>
        <td>
            YEAR<br>
            year
        </td>
    </tr>
    <tr>
        <td>
            MONTH<br>
            month
        </td>
    </tr>
    <tr>
        <td>
            DAY<br>
            day
        </td>
    </tr>
    <tr>
        <td>
            DATE<br>
            <strong>
                <u>
                    date
                </u>
            </strong>
        </td>
    </tr>
</table>

Bij deze tabel zijn er veel 1-op-veel relaties.

Afgeleide dimensiewaarden:

`YEAR` = `DATE.to_year()`

`QUARTER` = `DATE.to_quarter()`

`MONTH` = `DATE.to_month()`

`DAY` = `DATE.to_day()`

<table border="1">
    <tr>
        <td colspan="5" align="center">
            KLANT
        </td>
    </tr>
    <tr>
        <td>
            RETAILER_TYPE<br>
            retailer_type_code, retailer_type_en
        </td>
        <td>
            COUNTRY_CODE<br>
            zone
        </td>
        <td>
            SEGMENT<br>
            segment_code, segment_name, segment_description
        </td>
        <td>
            JOB_POSITION<br>
            position
        </td>
        <td>
            GENDER<br>
            gender
        </td>
    </tr>
    <tr>
        <td rowspan="4">
            CODE<br>
            retailer_code, retailer_code_mr, company_name
        </td>
    </tr>
    <tr>
        <td>
            CITY<br>
            city
        </td>
    </tr>
    <tr>
        <td>
            REGION<br>
            name
        </td>
    </tr>
    <tr>
        <td>
            POSTAL_ZONE<br>
            name
        </td>
    </tr>
    <tr>
        <td colspan="5">
            KLANT<br>
            <strong>
                <u>
                    retailer_site_code
                </u>
            </strong>, retailer_contact_code, first_name, last_name, extension, fax, e_mail, active_indicator, language, retailer_name, phone, address1, address2
        </td>
    </tr>
</table>
