# Luxon Business Days

![npm](https://img.shields.io/npm/v/luxon-business-days)
[![CircleCI](https://circleci.com/gh/amaidah/luxon-business-days/tree/master.svg?style=svg)](https://circleci.com/gh/amaidah/luxon-business-days/tree/master)
[![codecov](https://codecov.io/gh/amaidah/luxon-business-days/branch/master/graph/badge.svg)](https://codecov.io/gh/amaidah/luxon-business-days)
![luxon-business-days](https://badgen.net/bundlephobia/minzip/luxon-business-days)

Luxon Business Days is a Luxon plugin for calculating and manipulating business days.

Inspired by [moment-business-days](https://github.com/kalmecak/moment-business-days).

## Features

- Add business days to a standard luxon `DateTime` instance. For instance, to calculate the arrival date of a shipment.
- Customizable and extendable. Configure the business working days and holidays of your business.
- Uses holiday "matcher functions" avoiding the need to continually update holiday date configs every year.

## Install

Already using luxon:

```bash
yarn add luxon-business-days
```

```diff
- import { DateTime } from 'luxon';
+ import { DateTime } from 'luxon-business-days';
// Use DateTime as normal
```

Not already using luxon:

```bash
yarn add luxon luxon-business-days
```

```javascript
import { DateTime } from 'luxon-business-days';
// Use DateTime as normal
```

## Config

Default business days:

- Monday
- Tuesday
- Wednesday
- Thursday
- Friday

Default holidays (aka shipping holidays via UPS):

- New Year's Day
- Easter Day
- Memorial Day
- Independance Day
- Labor Day
- Thanksgiving Day
- Christmas Day

#### Configure business days

```javascript
import { DateTime } from 'luxon-business-days';

const dt = DateTime.local();

// [Mon, Thur, Fri, Sun]
const awesomeFourDayBusinessWeek = [1, 4, 5, 7];

dt.setupBusiness({ businessDays: awesomeFourDayBusinessWeek });
```

#### Configure holidays

Coming soon.

## Usage

Basic:

```javascript
import { DateTime } from 'luxon-business-days';

// Day before July 4
let dt = DateTime.local(2019, 7, 3);

dt = dt.plusBusiness(); // 7/5/19 - Friday
dt = dt.plusBusiness({ days: 2 }); // 7/9/19 - Tuesday (Skipped through Saturday/Sunday)

// Now do what you normally would with a DateTime instance.
```

## API

## Functions

<dl>
<dt><a href="#setupBusiness">setupBusiness([businessDays], [holidayMatchers])</a></dt>
<dd><p>Sets up business days and holiday matchers globally for all DateTime instances.</p>
</dd>
<dt><a href="#clearBusinessSetup">clearBusinessSetup()</a></dt>
<dd><p>Clears business setup from DateTime instance.</p>
</dd>
<dt><a href="#isHoliday">isHoliday()</a> ⇒ <code>boolean</code></dt>
<dd><p>Checks if DateTime instance is a holiday by checking against all holiday matchers.</p>
</dd>
<dt><a href="#isBusinessDay">isBusinessDay()</a> ⇒ <code>boolean</code></dt>
<dd><p>Checks if DateTime instance is a business day.</p>
</dd>
<dt><a href="#plusBusiness">plusBusiness([days])</a> ⇒ <code>DateTime</code></dt>
<dd><p>Adds business days to an existing DateTime instance.</p>
</dd>
</dl>

<a name="setupBusiness"></a>

## setupBusiness([businessDays], [holidayMatchers])
Sets up business days and holiday matchers globally for all DateTime instances.

**Kind**: global function  

| Param | Type | Default | Description |
| --- | --- | --- | --- |
| [businessDays] | <code>Array.&lt;number&gt;</code> | <code>DEFAULT_BUSINESS_DAYS</code> | The working business days for the business. |
| [holidayMatchers] | <code>Array.&lt;function()&gt;</code> | <code>DEFAULT_HOLIDAY_MATCHERS</code> | The holiday matchers used to check if a particular day is a holiday for the business. |

<a name="clearBusinessSetup"></a>

## clearBusinessSetup()
Clears business setup from DateTime instance.

**Kind**: global function  
<a name="isHoliday"></a>

## isHoliday() ⇒ <code>boolean</code>
Checks if DateTime instance is a holiday by checking against all holiday matchers.

**Kind**: global function  
<a name="isBusinessDay"></a>

## isBusinessDay() ⇒ <code>boolean</code>
Checks if DateTime instance is a business day.

**Kind**: global function  
<a name="plusBusiness"></a>

## plusBusiness([days]) ⇒ <code>DateTime</code>
Adds business days to an existing DateTime instance.

**Kind**: global function  

| Param | Type | Default | Description |
| --- | --- | --- | --- |
| [days] | <code>number</code> | <code>1</code> | The number of business days to add. |

