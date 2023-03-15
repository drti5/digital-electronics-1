# Lab 5: Vojtech Drtina

### D & T Flip-flops

1. Screenshot with simulated time waveforms. Try to simulate both D- and T-type flip-flops in a single testbench with a maximum duration of 350 ns, including reset. Always display all inputs and outputs (display the inputs at the top of the image, the outputs below them) at the appropriate time scale!

   ![your figure](https://github.com/drti5/digital-electronics-1/blob/main/05-ffs/t%2Bd_prubeh.PNG)

### JK Flip-flop

1. Listing of VHDL architecture for JK-type flip-flop. Always use syntax highlighting, meaningful comments, and follow VHDL guidelines:

```vhdl
architecture behavioral of jk_ff_rst is
    -- It must use this local signal instead of output ports
    -- because "out" ports cannot be read within the architecture
    signal sig_q : std_logic;
begin
    p_jk_ff_rst : process (clk) is
    begin
        if rising_edge(clk) then

            if (j = '0') then
                if (k = '0') then
                    sig_q <= sig_q;
                else 
                    sig_q <= '0';
                end if;
            else
                if (k = '0') then
                    sig_q <= '1';
                else 
                    sig_q <= not sig_q;
                end if;
            end if;            
        end if;
    end process p_jk_ff_rst;

    -- Output ports are permanently connected to local signal
    q     <= sig_q;
    q_bar <= not sig_q;
end architecture behavioral;
```

### Shift register

1. Image of `top` level schematic of the 4-bit shift register. Use four D-type flip-flops and connect them properly. The image can be drawn on a computer or by hand. Always name all inputs, outputs, components and internal signals!

   ![your figure](https://github.com/drti5/digital-electronics-1/blob/main/05-ffs/schema.png)
