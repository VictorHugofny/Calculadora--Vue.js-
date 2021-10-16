<template>
  <div class="calculator">
      <Display :value = "displayValue"/>
      <Button label ="AC" triple @onClick = "clearMemory"/>
      <Button label ="/" operation @onClick = "setOperation"/>
      <Button label ="7" @onClick = "AddDigit"/>
      <Button label ="8" @onClick = "AddDigit"/>
      <Button label ="9" @onClick = "AddDigit"/>
      <Button label ="*" @onClick = "setOperation" operation/>
      <Button label ="4" @onClick = "AddDigit"/>
      <Button label ="5" @onClick = "AddDigit"/>
      <Button label ="6" @onClick = "AddDigit"/>
      <Button label ="-" @onClick = "setOperation" operation/>
      <Button label ="1" @onClick = "AddDigit"/>
      <Button label ="2" @onClick = "AddDigit"/>
      <Button label ="3" @onClick = "AddDigit"/>
      <Button label ="+" operation @onClick = "setOperation" />
      <Button label ="0" @onClick = "AddDigit" double/>
      <Button label ="." @onClick = "setOperation" />
      <Button label ="=" operation @onClick = "setOperation"/>

  </div>
</template>

<script>
import Display from "../components/display.vue"
import Button from "../components/Button.vue"

export default {
    data: function(){
        return{
            displayValue: '0',
            clearDisplay: false,
            operation: null,
            values: [0,0],
            current: 0


        }
    },
    components: {Button, Display},
    methods: {
        clearMemory(){
            Object.assign(this.$data, this.$options.data())
        },
        setOperation(operation){
            console.log(operation)
        },
        AddDigit(n){
            console.log(n)
            if (n === "." && this.displayValue.includes('.')){
                return
            }
            const clearDisplay = this.displayValue === "0" || this.ClearDisplay
            const currentValue = clearDisplay ? "" : this.displayValue
            const displayValue = currentValue + n

            this.displayValue = displayValue
            this.clearDisplay = false

            if( n !== "."){
                const i = this.current
                const newValue = parseFloat(displayValue)
                this.values[i] = newValue
            }

}   
    }
}
</script>

<style>
.calculator{
    height: 320px;
    width: 235px;
    border-radius: 5px;
    overflow: hidden;

    display: grid;
    grid-template-columns: repeat(4, 25%) ;
    grid-template-rows: 1fr 48px 48px 48px  48px 48px;
}
</style>