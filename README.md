# Loginnext.js


import { useState } from "react";
import { Hidden, Lock, Rightarrow, Show } from "../common/Icon";
import { input } from "../common/Helper";

const Home = () => {
  // Maintain an array of visibility states for each input field
  const [hiddenStates, setHiddenStates] = useState(input.map(() => true));

  // Toggle visibility for a specific input field
  const toggleHidden = (index) => {
    setHiddenStates((prevStates) => {
      const newStates = [...prevStates];
      newStates[index] = !newStates[index];
      return newStates;
    });
  };

      


  return (
    <div className=" h-screen flex justify-center items-center px-5  max-md:px-4">
      <div className="max-w-[550px] w-full px-[30px] py-8 border-2 border-[rgba(0,0,0,0.20)] rounded-2xl text-center flex flex-col gap-[50px] max-sm:gap-5 max-sm:p-4">
        <div className="flex flex-col gap-[30px]">
          <div className="text-center font-Inter flex flex-col gap-[13px] max-md:gap-1">
            <p className="text-[#1D1D1B] text-4xl font-medium capitalize max-sm:text-3xl">
              Set new Password
            </p>
            <p className="must_be">Must be at least 8 characters.</p>
          </div>

          <div className="flex flex-col gap-4">
            {/* input div */}
            {input.map((items, index) => (
              <div
                key={index}
                className="h-[50px] rounded-[4px] border-2 border-[rgba(0,0,0,0.20)] flex items-center gap-[9px] pl-[10px] pr-[13px]"
              >
                <Lock />

                <input
                  type={hiddenStates[index] ? "password" : "text"}
                  className="text-[#1D1D1B] text-base font-normal leading-[150%] font-Inter outline-none w-full"
                  placeholder={items.placeholder}
                />

                <div onClick={() => toggleHidden(index)} className="">
                  {hiddenStates[index] ? <Show /> : <Hidden />}
                </div>
              </div>
            ))}
          </div>
        </div>
        <div className="flex flex-col gap-5 text-center">
          <button
            className="bg-[#386D96] rounded-lg w-full py-[11px] px-6 flex items-center gap-[10px] justify-center text-lg font-medium font-Inter capitalize text-white"
            type="submit"
          >
            Reset Password <Rightarrow />
          </button>

          <p className="must-be">Back to Sign In</p>
        </div>
      </div>
    </div>
  );
};

export default Home;
