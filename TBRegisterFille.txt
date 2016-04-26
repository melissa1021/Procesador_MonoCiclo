--------------------------------------------------------------------------------
-- Company: 
-- Engineer:
--
-- Create Date:   15:42:42 04/24/2016
-- Design Name:   
-- Module Name:   C:/Users/Melissa/Documents/Arquitectura/Ejercicios_Xilinx/Procesador_Mono_Ciclo/TBRegisterFille.vhd
-- Project Name:  Procesador_Mono_Ciclo
-- Target Device:  
-- Tool versions:  
-- Description:   
-- 
-- VHDL Test Bench Created by ISE for module: RegisterFille
-- 
-- Dependencies:
-- 
-- Revision:
-- Revision 0.01 - File Created
-- Additional Comments:
--
-- Notes: 
-- This testbench has been automatically generated using types std_logic and
-- std_logic_vector for the ports of the unit under test.  Xilinx recommends
-- that these types always be used for the top-level I/O of a design in order
-- to guarantee that the testbench will bind correctly to the post-implementation 
-- simulation model.
--------------------------------------------------------------------------------
library IEEE;
use IEEE.STD_LOGIC_1164.ALL;
use IEEE.STD_LOGIC_UNSIGNED.ALL;

-- Uncomment the following library declaration if using
-- arithmetic functions with Signed or Unsigned values
--USE ieee.numeric_std.ALL;
 
ENTITY TBRegisterFille IS
END TBRegisterFille;
 
ARCHITECTURE behavior OF TBRegisterFille IS 
 
    -- Component Declaration for the Unit Under Test (UUT)
 
    COMPONENT RegisterFille
    PORT(
         RS1 : IN  std_logic_vector(4 downto 0);
         RS2 : IN  std_logic_vector(4 downto 0);
         RD : IN  std_logic_vector(4 downto 0);
         RALU : IN  std_logic_vector(31 downto 0);
         CRS1 : OUT  std_logic_vector(31 downto 0);
         CRS2 : OUT  std_logic_vector(31 downto 0);
         RFreset : IN  std_logic
        );
    END COMPONENT;
    

   --Inputs
   signal RS1 : std_logic_vector(4 downto 0) := (others => '0');
   signal RS2 : std_logic_vector(4 downto 0) := (others => '0');
   signal RD : std_logic_vector(4 downto 0) := (others => '0');
   signal RALU : std_logic_vector(31 downto 0) := (others => '0');
   signal RFreset : std_logic := '0';

 	--Outputs
   signal CRS1 : std_logic_vector(31 downto 0) := (others => '0');
   signal CRS2 : std_logic_vector(31 downto 0)  := (others => '0');

   -- Clock period definitions
   --constant RFCLK_period : time := 10 ns;
 
BEGIN
 
	-- Instantiate the Unit Under Test (UUT)
   uut: RegisterFille PORT MAP (
          RS1 => RS1,
          RS2 => RS2,
          RD => RD,
          RALU => RALU,
          CRS1 => CRS1,
          CRS2 => CRS2,
          RFreset => RFreset
        );

   -- Clock process definitions
--   RFCLK_process :process
--   begin
--		RFCLK <= '0';
--		wait for RFCLK_period/2;
--		RFCLK <= '1';
--		wait for RFCLK_period/2;
--   end process;
 

   -- Stimulus process
   stim_proc: process
   begin
	    RFreset<='1';
      -- hold reset state for 100 ns.
      wait for 100 ns;


		RFreset<='0';
		
		--wait for 30 ns;

      --wait for clk_period*10;
		
		RS1 <="01000";
		RS2 <="10000";
		RD <="00110";
		RALU<="00000000000000000000000000000111";

      wait;
   end process;

END;
