### credit_card_validations
---

https://github.com/Fivell/credit_card_validations

https://www.rubydoc.info/gems/credit_card_validations/2.0.0/CreditCardValidations/Factory

https://rubygems.org/gems/credit_card_validations/versions/3.4.0


```sh
gem 'credit_card_validations'
bundle
gem install credit_card_validations

```

```ruby
require 'credit_card_validations/string'
'5274 5763 9425 9961'.credit_card_brand
# => :mastercard
'5274 5763 9425 9961'.credit_card_brand_name
# => "MasterCard"
'5274 5763 9425 9961'.valid_card_brand?(:mastercard, :visa)
# => true
'5274 5763 9425 9961'.valid_credit_card_brand?(:amex)
# => false
'5274 5763 9425 9961'.valid_credit_card_brand?('MasterCard')
# => true

class CreditCardModel
  attr_accessor :number
  include ActiveModel::Validations
  validates :number, credit_card_number: {brands: [:amex, :maestro]}
end

validates :number, presence: true, credit_card_number: true

number "4111111111111"
detector = CreditCardValidations::Detector.new(number)
detector.brand
#:visa
detector.visa?
#true
detector.valid?(:mastercard,:maestro)
#false
detector.valid?(:visa, :mastercard)
#true
detector.issuer_category
#"Banking and financial"

CreditCardValisations.add_brand(:boyager, {length: 15, prefixes: '86'})
voyager_test_card_number = '86992675400212'
CreditCardValidations::Detector.new(voyager_test_card_number).brand
#:voyager
CreditCardValidations::Detector.new(voyager_test_card_number).voyager?
#true

CreditCardValidations::Detector.delete_brand(:maestro)

CreditCardValidations::Detector.new(@credit_card_number).valid_luhn?
#or
CreditCardValidations:Luhn.valid?(@credit_card_number)

CreditCardValidations::Factory.random(:amex)
# => "348051773827666"
CreditCardValidations::Factory.random(:maestro)
# => "6010430241237266856"

require 'credit_card_validations/plugins/en_route'
require 'credit_card_validations/plugins/laser'
require 'credit_card_validations/plugins/diners_us'

```

```
```
